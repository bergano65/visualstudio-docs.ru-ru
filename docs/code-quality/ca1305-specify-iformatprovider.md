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
ms.openlocfilehash: a9f6c8fd44749de43d86bf8037df0130ad682321
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235037"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305. Указывайте IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Метод или конструктор вызывает один или несколько элементов, которые имеют перегрузки, принимающие <xref:System.IFormatProvider?displayProperty=fullName> параметр, а метод или конструктор не вызывает перегрузку, которая <xref:System.IFormatProvider> принимает параметр.

Это правило игнорирует вызовы методов .NET, которые задокументированы как пропускают <xref:System.IFormatProvider> параметр. Правило также игнорирует следующие методы.

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Описание правила

Если объект <xref:System.IFormatProvider> или не указан, то значение по умолчанию, предоставляемое перегруженным членом, может не иметь желаемого результата во всех языковых стандартах. <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> Кроме того, члены .NET выбирают язык и региональные параметры по умолчанию и форматирование на основе допущений, которые могут быть неправильными для вашего кода. Чтобы убедиться в том, что код работает правильно для ваших сценариев, необходимо предоставить сведения, относящиеся к культуре, в соответствии со следующими рекомендациями.

- Если значение будет отображаться для пользователя, используйте текущий язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Если значение будет сохранено и доступно программное обеспечение (сохраненное в файле или базе данных), используйте инвариантный язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Если вы не узнаете назначение значения, укажите в качестве потребителя или поставщика данных культуру.

Даже если поведение перегруженного элемента по умолчанию подходит для ваших потребностей, лучше вызвать перегрузку, зависящую от языка и региональных параметров, чтобы обеспечить самодокументирование и упростить обслуживание кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, используйте перегрузку, которая принимает <xref:System.IFormatProvider> аргумент. Или используйте [ C# интерполяцию строки](/dotnet/csharp/tutorials/string-interpolation) и передайте <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> ее в метод.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение от этого правила можно отключить, если известно, что используется формат по умолчанию, а поддержка кода не является важным приоритетом разработки.

## <a name="example"></a>Пример

В следующем коде `example1` строка нарушает правило CA1305. Строка удовлетворяет правилу CA1305 путем передачи <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, которая реализует <xref:System.IFormatProvider>, в <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. `example2` Строка удовлетворяет правилу CA1305, передавая строку с интерполяцией в <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>. `example3`

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

- [CA1304 Укажите CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>См. также

- [Использование класса CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)