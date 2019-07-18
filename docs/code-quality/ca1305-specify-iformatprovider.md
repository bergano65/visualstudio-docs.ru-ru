---
title: CA1305. Указывайте IFormatProvider
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: eda86085a5a2b8ba8e42116005890d2bda0b1dca
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714686"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305. Указывайте IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Метод или конструктор вызывает один или несколько членов, которые имеют перегрузки, принимающие <xref:System.IFormatProvider?displayProperty=fullName> параметра и этот метод или конструктор не вызывает перегрузку, принимающую <xref:System.IFormatProvider> параметра.

Это правило не учитывает вызовы методов .NET, задокументированы в качестве пропуск <xref:System.IFormatProvider> параметра. Правило также игнорирует следующие методы:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Описание правила

Когда <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> или <xref:System.IFormatProvider> не предоставляется значение по умолчанию, поставляемое перегруженным членом, возможно, не нужных во всех языковых стандартах. Кроме того члены .NET выберите язык и региональные параметры по умолчанию и исходя из предположения, которые могут быть неправильными в коде. Чтобы убедиться, что код работает правильно для сценариев, необходимо предоставить сведения об особенностях языка и региональных параметров в соответствии с приведенным ниже рекомендациям:

- Если значение будет отображаться для пользователя, используйте текущий язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Если значение будет храниться и использоваться программой, (сохраняется в файле или базе данных), использующие инвариантный язык. См. раздел <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Если вы не знаете назначение значения, у потребителя данных или поставщик указать язык и региональные параметры.

Даже если перегруженным членом по умолчанию не подходит для ваших потребностей, лучше явно вызвать перегрузку конкретного языка и региональных параметров, чтобы ваш код самодокументируемыми и более простую обслуживаемую.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, используйте перегрузку, принимающую <xref:System.IFormatProvider> аргумент. Также можно использовать [C# интерполированную строку](/dotnet/csharp/tutorials/string-interpolation) и передать его в <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, когда известно, что формат по умолчанию, является правильным выбором и удобства поддержки кода не является важным разработки приоритет.

## <a name="example"></a>Пример

В следующем коде `example1` строки нарушает правило CA1305. `example2` Строка должна соответствовать правило CA1305 путем передачи <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, который реализует <xref:System.IFormatProvider>, <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. `example3` Строка должна соответствовать правило CA1305 путем передачи интерполированной строки в <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>Связанные правила

- [CA1304: Укажите CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>См. также

- [С помощью класса CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)