---
title: 'CA1032: реализуйте стандартные конструкторы исключения'
ms.date: 11/04/2016
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
ms.openlocfilehash: d140ab9f9ee5ef27332c59e30920fa89aebefdde
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: реализуйте стандартные конструкторы исключения
|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип расширяет <xref:System.Exception?displayProperty=fullName> и не объявляет все обязательные конструкторы.

## <a name="rule-description"></a>Описание правила
 Типы исключений должны реализовывать следующие конструкторы:

-   открытые NewException()

-   открытые NewException(string)

-   открытый NewException (string, Exception)

-   защищенным, либо закрытым NewException (SerializationInfo, StreamingContext)

 Для правильной обработки исключений необходимо предоставить полный набор конструкторов. Например, конструктор, который имеет сигнатуру `NewException(string, Exception)` используется для создания исключения, вызванные другие исключения. Без этого конструктора не может создать и вызвать экземпляр пользовательского исключения, которое содержит внутреннее исключение (вложенная) — в таком случае делать какие управляемого кода. Первые три конструктора исключений являются открытыми по соглашению. Четвертый конструктор является защищенным в незапечатанных классов и закрытым в запечатанных классов. Дополнительные сведения см. в разделе [CA2229: Применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, добавьте отсутствующий конструктор на исключение и убедитесь в том, что они имеют правильный уровень доступа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно отключать предупреждение из этого правила, если возникает нарушение с помощью другой уровень доступа для открытых конструкторов.

## <a name="example"></a>Пример
 В следующем примере содержится тип исключения, которое нарушает это правило и правильно реализованный тип исключения.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]