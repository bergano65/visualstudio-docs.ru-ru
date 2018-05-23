---
title: 'CA1032: реализуйте стандартные конструкторы исключения'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6cd6922cae5e2d182a279e2d1637a19f8572468
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: реализуйте стандартные конструкторы исключения

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип расширяет <xref:System.Exception?displayProperty=fullName> , но не объявляет все обязательные конструкторы.

## <a name="rule-description"></a>Описание правила

Типы исключений должны реализовывать следующие три конструктора:

- открытые NewException()

- открытые NewException(string)

- открытый NewException (string, Exception)

Кроме того, если вы используете устаревший FxCop статического анализа кода как отличие от [анализаторы FxCop на основе Roslyn](../code-quality/roslyn-analyzers-overview.md), отсутствие четвертый конструктор также создает нарушение:

- защищенным, либо закрытым NewException (SerializationInfo, StreamingContext)

Для правильной обработки исключений необходимо предоставить полный набор конструкторов. Например, конструктор, который имеет сигнатуру `NewException(string, Exception)` используется для создания исключения, вызванные другие исключения. Без этого конструктора не может создать и вызвать экземпляр пользовательского исключения, которое содержит внутреннее исключение (вложенная), это следует делать какие управляемый код в такой ситуации.

Первые три конструктора исключений являются открытыми по соглашению. Четвертый конструктор является защищенным в незапечатанных классов и закрытым в запечатанных классов. Дополнительные сведения см. в разделе [CA2229: Применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение данного правила, добавьте отсутствующий конструктор на исключение и убедитесь в том, что они имеют правильный уровень доступа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Можно безопасно отключать предупреждение из этого правила, если возникает нарушение с помощью другой уровень доступа для открытых конструкторов. Кроме того, можно отключить предупреждения для `NewException(SerializationInfo, StreamingContext)` конструктор при создании переносимой библиотеки классов (PCL).

## <a name="example"></a>Пример

В следующем примере содержится тип исключения, которое нарушает это правило и правильно реализованный тип исключения.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>См. также

[CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)