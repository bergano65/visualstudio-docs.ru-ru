---
title: CA1305. Укажите IFormatProvider | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 93bf7f17f77008ce8e9898c1871926edf2e8439f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694774"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305. Указывайте IFormatProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод или конструктор вызывает один или несколько членов, которые имеют перегрузки, принимающие <xref:System.IFormatProvider?displayProperty=fullName> параметра и этот метод или конструктор не вызывает перегрузку, принимающую <xref:System.IFormatProvider> параметра. Это правило пропускает вызовы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] методов, описанных как пропускающие <xref:System.IFormatProvider> параметра, кроме следующих методов:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Описание правила
 Когда <xref:System.Globalization.CultureInfo?displayProperty=fullName> или <xref:System.IFormatProvider> не предоставляется значение по умолчанию, поставляемое перегруженным членом, возможно, не нужных во всех языковых стандартах. Кроме того [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] члены выбирают язык и региональные параметры по умолчанию и исходя из предположения, которые могут быть неправильными в коде. Чтобы убедиться, что код работает правильно для сценариев, необходимо предоставить сведения об особенностях языка и региональных параметров в соответствии с приведенным ниже рекомендациям:

- Если значение будет отображаться для пользователя, используйте текущий язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Если значение будет храниться и использоваться программой, (сохраняется в файле или базе данных), использующие инвариантный язык. См. раздел <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Если вы не знаете назначение значения, у потребителя данных или поставщик указать язык и региональные параметры.

  Обратите внимание, что <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> используется только для извлечения локализованных ресурсов с помощью экземпляра <xref:System.Resources.ResourceManager?displayProperty=fullName> класса.

  Даже если перегруженным членом по умолчанию не подходит для ваших потребностей, лучше явно вызвать перегрузку конкретного языка и региональных параметров, чтобы ваш код самодокументируемыми и более простую обслуживаемую.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, используйте перегрузку, принимающую <xref:System.Globalization.CultureInfo> или <xref:System.IFormatProvider> и указан аргумент согласно рекомендациям, которые были указаны ранее.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, когда известно, что поставщик языка и региональных параметров или формат по умолчанию является правильным выбором и удобства поддержки кода не является важным разработки приоритет.

## <a name="example"></a>Пример
 В следующем примере `BadMethod` вызывает два нарушения этого правила. `GoodMethod` исправляет первое нарушение, передав инвариантного языка и региональных параметров для <xref:System.String.Compare%2A>и исправляет нарушение второй путем передачи текущего языка и региональных параметров для <xref:System.String.ToLower%2A> поскольку `string3` отображается для пользователя.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Пример
 В следующем примере показано влияние текущего языка и региональных параметров по умолчанию <xref:System.IFormatProvider> установлен по <xref:System.DateTime> типа.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 В этом примере формируются следующие данные:

 **6/4/1900 Г., 12:15:12 PM**
**06/04/1900 Г., 12:15:12**
## <a name="related-rules"></a>Связанные правила
 [CA1304: Укажите CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>См. также
 [NIB: С помощью класса CultureInfo](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
