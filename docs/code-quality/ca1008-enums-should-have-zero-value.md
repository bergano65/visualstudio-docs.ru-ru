---
title: 'CA1008: перечисляемые типы должны иметь нулевое значение'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 60c5e6e93c8ededc7d08d3b917f8066148f133f7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551799"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: перечисляемые типы должны иметь нулевое значение

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое — при появлении предложения добавить **None** значение к перечислению без флага. Критическое — если приглашение переименовать или удалить все значения перечисления.|

## <a name="cause"></a>Причина

Перечисление без примененного <xref:System.FlagsAttribute?displayProperty=fullName> не определяет член, имеющий значение равно нулю, или перечисление с примененного <xref:System.FlagsAttribute> определяет элемент, имеет нулевое значение, но его имя не является «None» или перечисление определяет несколько нулевым значением элементы.

## <a name="rule-description"></a>Описание правила

Значение по умолчанию неинициализированного перечисления, так же, как и других типов значений, равно нулю. Перечисление без флагов атрибутов должно определять член с нулевым значением, таким образом, значение по умолчанию — допустимое значение перечисления. При необходимости, имя члена «None». В противном случае присвойте ноль наиболее часто используемых элементов. По умолчанию Если значение первого элемента перечисления не указано в объявлении, его значение равно нулю.

Если перечисление с <xref:System.FlagsAttribute> применения определяет член с нулевым значением, его имя должно быть «None», чтобы указать, что значения не заданы в перечислении. С помощью член с нулевым значением, для каких-либо других целях — в отличие от использования <xref:System.FlagsAttribute> в том, что и и или битовые операторы смысла для члена. Это означает, что только одному члену должны назначаться нулевое значение. При возникновении несколько элементов с нулевым значением в перечислении флагами в качестве атрибутов, `Enum.ToString()` возвращает неверные результаты для членов, которые не равны нулю.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила для перечислений без флаги атрибутов, определите член, имеющий значение равно нулю; Это не критическое изменение. Для атрибутов флаги перечисления, которые определяют член с нулевым значением назовите этот член «None» и удалите любые другие члены, которые имеют нулевое значение; Это критическое изменение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Не отключайте предупреждение из этого правила, за исключением перечислений флагов в качестве атрибутов, ранее поставленных.

## <a name="example"></a>Пример

В следующем примере показано два перечисления, которые удовлетворяют правилу и перечисления, `BadTraceOptions`, который нарушает правило.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA2217: не следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: не следует называть значения перечислений именем "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: не добавляйте имя типа перед перечисляемыми значениями](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: хранилище перечислений должно иметь тип Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: следует помечать перечисления атрибутом FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также

- <xref:System.Enum?displayProperty=fullName>