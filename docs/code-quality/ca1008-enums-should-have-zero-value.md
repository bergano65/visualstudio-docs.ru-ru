---
title: CA1008. Перечисляемые типы должны иметь нулевое значение
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 502033d2adffd640d2af6ee8d36b0c0f3cd71472
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547929"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008. Перечисляемые типы должны иметь нулевое значение

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое — при появлении запроса на добавление значения **None** к перечислению без флага. Критическое — при появлении запроса на переименование или удаление любых значений перечисления.|

## <a name="cause"></a>Причина

Перечисление без примененного <xref:System.FlagsAttribute?displayProperty=fullName> параметра не определяет элемент, имеющий нулевое значение. Или перечисление, имеющее примененное <xref:System.FlagsAttribute> свойство, определяет член, имеющий нулевое значение, но его имя не равно "None". Или перечисление определяет несколько элементов с нулевым значением.

По умолчанию это правило рассматривает только видимые извне перечисления, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Значение по умолчанию для неинициализированного перечисления, как и для других типов значений, равно нулю. Перечисление без флагов должно определять член, имеющий нулевое значение, чтобы значение по умолчанию было допустимым значением перечисления. При необходимости присвойте элементу имя "None". В противном случае необходимо присвоить значение "ноль" наиболее часто используемому члену. По умолчанию, если значение первого члена перечисления не задано в объявлении, его значение равно нулю.

Если перечисление <xref:System.FlagsAttribute> с примененным атрибутом определяет элемент с нулевым значением, его имя должно быть "None", чтобы показать, что в перечислении не заданы значения. Использование элемента с нулевым значением <xref:System.FlagsAttribute> в любых других целях противоречит использованию метода в том, что битовые операторы and и OR не имеют смысла с элементом. Это означает, что только одному члену должно быть присвоено нулевое значение. Если несколько элементов с нулевым значением встречаются в перечислении с атрибутом Flags `Enum.ToString()` , возвращает неверные результаты для элементов, которые не равны нулю.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила для перечислений, не являющихся флагами, определите элемент, имеющий нулевое значение. Это некритическое изменение. Для перечислений с атрибутом Flags, которые определяют член с нулевым значением, присвойте этому элементу значение "None" и удалите все остальные члены, имеющие нулевые значения. Это критическое изменение.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не отключайте предупреждение из этого правила, за исключением перечислений с атрибутом Flags, которые были отправлены ранее.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1008.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показаны два перечисления, которые удовлетворяют правилу, и перечисление `BadTraceOptions`, которое нарушает правило.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA2217: Не помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Не наименование значений enum "reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712 Не добавляйте значения перечисления в качестве префикса имени типа](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: Хранилище перечислений должно иметь тип Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027 Пометьте перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.Enum?displayProperty=fullName>