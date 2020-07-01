---
title: 'CA1008: enums должно иметь нулевое значение | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ca58938a55330243315529e9c7990b59d1a6fe5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548347"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008. Перечисляемые типы должны иметь нулевое значение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое — при появлении запроса на добавление значения **None** к перечислению без флага. Критическое — при появлении запроса на переименование или удаление любых значений перечисления.|

## <a name="cause"></a>Причина
 Перечисление без примененного <xref:System.FlagsAttribute?displayProperty=fullName> параметра не определяет член, имеющий нулевое значение, или перечисление, имеющее примененное <xref:System.FlagsAttribute> Определение элемента, имеющего нулевое значение, но его имя не равно "None", либо перечисление определяет несколько элементов с нулевым значением.

## <a name="rule-description"></a>Описание правила
 Значение по умолчанию для неинициализированного перечисления, как и для других типов значений, равно нулю. Перечисление без флагов − должно определять член, имеющий нулевое значение, чтобы значение по умолчанию было допустимым значением перечисления. При необходимости присвойте элементу имя "None". В противном случае необходимо присвоить значение "ноль" наиболее часто используемому члену. Обратите внимание, что по умолчанию, если значение первого члена перечисления не задано в объявлении, его значение равно нулю.

 Если перечисление с <xref:System.FlagsAttribute> примененным атрибутом определяет элемент с нулевым значением, его имя должно быть "None", чтобы показать, что в перечислении не заданы значения. Использование элемента с нулевым значением в любых других целях противоречит использованию метода <xref:System.FlagsAttribute> в том, что битовые ОПЕРАТОРЫ and и OR не имеют смысла с элементом. Это означает, что только одному члену должно быть присвоено нулевое значение. Обратите внимание, что если несколько элементов с нулевым значением встречаются в перечислении с атрибутом Flags, `Enum.ToString()` возвращает неверные результаты для элементов, которые не равны нулю.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила для перечислений без флагов −, определите элемент, имеющий нулевое значение. Это некритическое изменение. Для перечислений с атрибутом Flags, которые определяют член с нулевым значением, присвойте этому элементу значение "None" и удалите все остальные члены, имеющие нулевые значения. Это критическое изменение.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, за исключением перечислений с атрибутом Flags, которые были отправлены ранее.

## <a name="example"></a>Пример
 В следующем примере показаны два перечисления, которые удовлетворяют правилу, и перечисление, `BadTraceOptions` которое нарушает правило.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2217. Не помечайте перечисляемые типы с помощью FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700. Не присваивайте перечисляемым значениям имя Reserved](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712. Не добавляйте имя типа перед перечисляемыми значениями](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028. Хранилище перечисляемых типов должно относиться к типу Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027. Пометьте перечисляемые типы с помощью FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>См. также
 <xref:System.Enum?displayProperty=fullName>
