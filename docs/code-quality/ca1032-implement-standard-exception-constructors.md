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
ms.openlocfilehash: 7baf13eb9125b273ad8fb1265a65eb7b053238a1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922398"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032. Реализуйте стандартные конструкторы исключений

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип расширяет <xref:System.Exception?displayProperty=fullName> , но не объявляет все необходимые конструкторы.

## <a name="rule-description"></a>Описание правила

Типы исключений, должны реализовывать следующие три конструктора:

- открытый NewException()

- открытый NewException(string)

- открытый NewException (string, исключений)

Кроме того, если вы используете устаревший FxCop статического анализа кода как отличие от [анализаторов на базе Roslyn FxCop](../code-quality/roslyn-analyzers-overview.md), отсутствие четвертый конструктор также создает нарушение:

- защищенный или закрытый NewException (SerializationInfo, StreamingContext)

Для правильной обработки исключений необходимо предоставить полный набор конструкторов. Например, конструктор, который имеет сигнатуру `NewException(string, Exception)` используется для создания исключения, вызванные другие исключения. Без этого конструктора нельзя создать и вызвать экземпляр пользовательского исключения, которое содержит внутреннее исключение (вложенная), это следует делать какие управляемого кода в такой ситуации.

Первые три конструктора исключений являются открытыми по соглашению. Четвертый конструктор является защищенным в незапечатанных классов и закрытым в запечатанных классах. Дополнительные сведения см. в разделе [CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, добавьте отсутствующий конструктор на исключение и убедитесь, что они имеют правильный уровень доступа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, когда возникает нарушение с помощью другой уровень доступа для открытых конструкторов. Кроме того, можно отключить предупреждения для `NewException(SerializationInfo, StreamingContext)` конструктор при создании переносимой библиотеки классов (PCL).

## <a name="example"></a>Пример

В следующем примере содержится тип исключения, который нарушает это правило и правильно реализованный тип исключения.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>См. также

[CA2229: реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)