---
title: 'CA1304: указание CultureInfo | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d874d69f36fc8520a7cfbe3e946116c2d85ed88f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539065"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304. Указывайте CultureInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод или конструктор вызывает член, имеющий перегрузку, принимающую <xref:System.Globalization.CultureInfo?displayProperty=fullName> параметр, а метод или конструктор не вызывает перегрузку, которая принимает <xref:System.Globalization.CultureInfo> параметр. Это правило игнорирует вызовы следующих методов:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Описание правила
 Если <xref:System.Globalization.CultureInfo> объект или <xref:System.IFormatProvider?displayProperty=fullName> не указан, то значение по умолчанию, предоставляемое перегруженным членом, может не иметь желаемого результата во всех языковых стандартах. Кроме того, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] члены выбирают язык и региональные параметры по умолчанию и форматирование на основе допущений, которые могут быть неправильными для вашего кода. Чтобы код правильно работал в ваших сценариях, необходимо предоставить сведения, относящиеся к культуре, в соответствии со следующими рекомендациями.

- Если значение будет отображаться для пользователя, используйте текущий язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Если значение будет храниться и доступно по программному обеспечению, то есть сохраненному в файле или базе данных, используется инвариантный язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Если вы не узнаете назначение значения, укажите в качестве потребителя или поставщика данных культуру.

  Обратите внимание, что <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> используется только для получения локализованных ресурсов с помощью экземпляра <xref:System.Resources.ResourceManager?displayProperty=fullName> класса.

  Даже если поведение перегруженного элемента по умолчанию подходит для ваших потребностей, лучше вызвать перегрузку, зависящую от языка и региональных параметров, чтобы обеспечить самодокументирование и упростить обслуживание кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, используйте перегрузку, которая принимает <xref:System.Globalization.CultureInfo> или, <xref:System.IFormatProvider> и укажите аргумент в соответствии с приведенными выше рекомендациями.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение в этом правиле можно отключить, если известно, что поставщик языка и региональных параметров по умолчанию является верным выбором, а поддержка кода не является важным приоритетом разработки.

## <a name="example"></a>Пример
 В следующем примере `BadMethod` приводит к двум нарушениям этого правила. `GoodMethod`устраняет первое нарушение, передавая инвариантный язык и региональные параметры в System. String. Compare и исправляет второе нарушение, передавая текущий язык и региональные параметры в, <xref:System.String.ToLower%2A> поскольку `string3` отображается для пользователя.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Пример
 В следующем примере показано воздействие текущего языка и региональных параметров на значение по умолчанию <xref:System.IFormatProvider> , выбранное <xref:System.DateTime> типом.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 В этом примере формируются следующие данные:

 **6/4/1900 12:15:12 РМ** 
 **06/04/1900 12:15:12**
## <a name="related-rules"></a>Связанные правила
 [CA1305. Указывайте IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>См. также
 [NIB: использование класса CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
