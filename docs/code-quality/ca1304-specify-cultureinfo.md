---
title: CA1304. Указывайте CultureInfo
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1fe4ebce3a49c4aa626515e22eacd1c8e263847
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797501"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304. Указывайте CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Метод или конструктор вызывает член, имеющий перегрузку, принимающую <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> параметра и этот метод или конструктор не вызывает перегрузку, принимающую <xref:System.Globalization.CultureInfo> параметра. Это правило пропускает вызовы следующих методов:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Описание правила

Когда <xref:System.Globalization.CultureInfo> или <xref:System.IFormatProvider?displayProperty=nameWithType> не предоставляется значение по умолчанию, поставляемое перегруженным членом, возможно, не нужных во всех языковых стандартах. Кроме того члены .NET Framework выберите язык и региональные параметры по умолчанию и исходя из предположения, которые могут быть неправильными в коде. Чтобы убедиться, что код работает правильно для сценариев, необходимо предоставить сведения об особенностях языка и региональных параметров в соответствии с приведенным ниже рекомендациям:

- Если значение будет отображаться для пользователя, используйте текущий язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Если значение будет храниться и использоваться программой, то есть сохраняется в файл или базу данных, использующие инвариантный язык. См. раздел <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Если вы не знаете назначение значения, у потребителя данных или поставщик указать язык и региональные параметры.

Даже если перегруженным членом по умолчанию не подходит для ваших потребностей, лучше явно вызвать перегрузку конкретного языка и региональных параметров, чтобы ваш код самодокументируемыми и более простую обслуживаемую.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> используется только для извлечения локализованных ресурсов с помощью экземпляра <xref:System.Resources.ResourceManager?displayProperty=nameWithType> класса.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, используйте перегрузку, принимающую <xref:System.Globalization.CultureInfo> аргумент.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, когда известно, что язык и региональные параметры по умолчанию, является правильным выбором и удобства поддержки кода не является важным разработки приоритет.

## <a name="example-showing-how-to-fix-violations"></a>Пример, показывающий, как устранить нарушения

В следующем примере `BadMethod` вызывает два нарушения этого правила. `GoodMethod` исправляет первое нарушение, передав инвариантного языка и региональных параметров для <xref:System.String.Compare%2A?displayProperty=nameWithType>и исправляет нарушение второй путем передачи текущего языка и региональных параметров для <xref:System.String.ToLower%2A?displayProperty=nameWithType> поскольку `string3` отображается для пользователя.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Пример демонстрирует Форматированные выходные данные

В следующем примере показано влияние текущего языка и региональных параметров по умолчанию <xref:System.IFormatProvider> установлен по <xref:System.DateTime> типа.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

В этом примере выводятся следующие данные:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Связанные правила

- [CA1305: Укажите IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>См. также

- [С помощью класса CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)