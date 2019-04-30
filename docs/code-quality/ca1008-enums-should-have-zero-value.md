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
ms.openlocfilehash: 4bb79d2944bdb49c59fd53fb30e1497c57c5c516
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779656"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008. Перечисляемые типы должны иметь нулевое значение

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое — при появлении предложения добавить **None** значение к перечислению без флага. Критическое — если приглашение переименовать или удалить все значения перечисления.|

## <a name="cause"></a>Причина

Перечисление без примененного <xref:System.FlagsAttribute?displayProperty=fullName> не определяет элемент, который имеет нулевое значение. Или, перечисление, которое имеет примененного <xref:System.FlagsAttribute> определяет элемент, имеет нулевое значение, но его имя не является «None». Или перечисление определяет несколько членов с нулевым значением.

По умолчанию это правило считывает только видимое извне перечисления, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Значение по умолчанию неинициализированного перечисления, так же, как и других типов значений, равно нулю. Перечисление без флагов атрибутов должно определять член с нулевым значением, таким образом, значение по умолчанию — допустимое значение перечисления. При необходимости, имя члена «None». В противном случае присвойте ноль наиболее часто используемых элементов. По умолчанию Если значение первого элемента перечисления не указано в объявлении, его значение равно нулю.

Если перечисление с <xref:System.FlagsAttribute> применения определяет член с нулевым значением, его имя должно быть «None», чтобы указать, что значения не заданы в перечислении. С помощью член с нулевым значением, для каких-либо других целях — в отличие от использования <xref:System.FlagsAttribute> в том, что и и или битовые операторы смысла для члена. Это означает, что только одному члену должны назначаться нулевое значение. При возникновении несколько элементов с нулевым значением в перечислении флагами в качестве атрибутов, `Enum.ToString()` возвращает неверные результаты для членов, которые не равны нулю.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила для перечислений без флаги атрибутов, определите член, имеющий значение равно нулю; Это не критическое изменение. Для атрибутов флаги перечисления, которые определяют член с нулевым значением назовите этот член «None» и удалите любые другие члены, которые имеют нулевое значение; Это критическое изменение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Не отключайте предупреждение из этого правила, за исключением перечислений флагов в качестве атрибутов, ранее поставленных.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1008.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показано два перечисления, которые удовлетворяют правилу и перечисления, `BadTraceOptions`, который нарушает правило.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA2217: Не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Не значения перечислений именем «Reserved»](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Не добавляйте префикс в виде значения перечисления с именем типа](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: Хранилище перечислений должно иметь тип Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: СЛЕДУЕТ Помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.Enum?displayProperty=fullName>