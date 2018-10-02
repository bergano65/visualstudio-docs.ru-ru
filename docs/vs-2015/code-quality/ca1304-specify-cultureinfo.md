---
title: 'CA1304: Укажите CultureInfo | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 149ab03c1ee33d8aaf5aae30ddf56150279c4052
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592001"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: укажите CultureInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1304: укажите CultureInfo](https://docs.microsoft.com/visualstudio/code-quality/ca1304-specify-cultureinfo).

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод или конструктор вызывает член, имеющий перегрузку, принимающую <xref:System.Globalization.CultureInfo?displayProperty=fullName> параметра и этот метод или конструктор не вызывает перегрузку, принимающую <xref:System.Globalization.CultureInfo> параметра. Это правило пропускает вызовы следующих методов:

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Описание правила
 Когда <xref:System.Globalization.CultureInfo> или <xref:System.IFormatProvider?displayProperty=fullName> не предоставляется значение по умолчанию, поставляемое перегруженным членом, возможно, не нужных во всех языковых стандартах. Кроме того [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] члены выбирают язык и региональные параметры по умолчанию и исходя из предположения, которые могут быть неправильными в коде. Чтобы убедиться, что код работает правильно для сценариев, необходимо предоставить сведения об особенностях языка и региональных параметров в соответствии с приведенным ниже рекомендациям:

-   Если значение будет отображаться для пользователя, используйте текущий язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

-   Если значение будет храниться и использоваться программой, то есть сохраняется в файл или базу данных, использующие инвариантный язык. См. раздел <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

-   Если вы не знаете назначение значения, у потребителя данных или поставщик указать язык и региональные параметры.

 Обратите внимание, что <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> используется только для извлечения локализованных ресурсов с помощью экземпляра <xref:System.Resources.ResourceManager?displayProperty=fullName> класса.

 Даже если перегруженным членом по умолчанию не подходит для ваших потребностей, лучше явно вызвать перегрузку конкретного языка и региональных параметров, чтобы ваш код самодокументируемыми и более простую обслуживаемую.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, используйте перегрузку, принимающую <xref:System.Globalization.CultureInfo> или <xref:System.IFormatProvider> и указан аргумент согласно рекомендациям, которые были указаны ранее.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, когда известно, что поставщик языка и региональных параметров или формат по умолчанию, является правильным выбором и удобства поддержки кода не является важным разработки приоритет.

## <a name="example"></a>Пример
 В следующем примере `BadMethod` вызывает два нарушения этого правила. `GoodMethod` исправляет первое нарушение, передав методу System.String.Compare инвариантного языка и региональных параметров и исправляет нарушение второй путем передачи текущего языка и региональных параметров для <xref:System.String.ToLower%2A> поскольку `string3` отображается для пользователя.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Пример
 В следующем примере показано влияние текущего языка и региональных параметров по умолчанию <xref:System.IFormatProvider> установлен по <xref:System.DateTime> типа.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 В этом примере формируются следующие данные:

 **6/4/1900 Г., 12:15:12 PM**
**06/04/1900 Г., 12:15:12**
## <a name="related-rules"></a>Связанные правила
 [CA1305: укажите IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>См. также
 [NIB: С помощью класса CultureInfo](http://msdn.microsoft.com/en-us/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)



