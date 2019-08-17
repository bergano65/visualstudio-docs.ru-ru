---
title: CA1032. Реализуйте стандартные конструкторы исключений
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b294b267aa7bb1a2912ed42807ac0f878c87838
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547661"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032. Реализуйте стандартные конструкторы исключений

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип расширяет <xref:System.Exception?displayProperty=fullName> , но не объявляет все необходимые конструкторы.

## <a name="rule-description"></a>Описание правила

Типы исключений должны реализовывать следующие три конструктора:

- общедоступная Невексцептион ()

- Public Невексцептион (строка)

- Public Невексцептион (строка, исключение)

Кроме того, если выполняется устаревший анализ FxCop в отличие от [анализаторов FxCop на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md), отсутствие четвертого конструктора также приводит к нарушению.

- protected или Private Невексцептион (SerializationInfo, StreamingContext)

Для правильной обработки исключений необходимо предоставить полный набор конструкторов. Например, конструктор с сигнатурой `NewException(string, Exception)` используется для создания исключений, вызванных другими исключениями. Без этого конструктора нельзя создать и вызвать экземпляр пользовательского исключения, содержащего внутреннее (вложенное) исключение, которое в таком случае должно делать управляемый код.

Первые три конструктора исключений являются общедоступными по соглашению. Четвертый конструктор защищен в незапечатанных классах и закрыт в запечатанных классах. Дополнительные сведения см. в [разделе CA2229: Реализуйте конструкторы](../code-quality/ca2229-implement-serialization-constructors.md)сериализации.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, добавьте недостающие конструкторы в исключение и убедитесь, что они имеют правильную доступность.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение из этого правила можно отключить, если нарушение вызвано использованием другого уровня доступа для открытых конструкторов. Кроме того, можно отключить предупреждение для `NewException(SerializationInfo, StreamingContext)` конструктора, если вы создаете переносимую библиотеку классов (PCL).

## <a name="example"></a>Пример

В следующем примере содержится тип исключения, нарушающий это правило, и тип исключения, который был правильно реализован.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>См. также

[CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)