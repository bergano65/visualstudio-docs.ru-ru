---
title: 'CA1032: Реализуйте стандартные конструкторы исключения | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4d8c2f4439cf63f0bab7294898c96b2acb742e7d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591615"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: реализуйте стандартные конструкторы исключения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1032: реализуйте стандартные конструкторы исключения](https://docs.microsoft.com/visualstudio/code-quality/ca1032-implement-standard-exception-constructors).

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип расширяет <xref:System.Exception?displayProperty=fullName> и не объявляет все необходимые конструкторы.

## <a name="rule-description"></a>Описание правила
 Типы исключений, должны реализовывать следующие конструкторы:

-   открытый NewException()

-   открытый NewException(string)

-   открытый NewException (string, исключений)

-   защищенный или закрытый NewException (SerializationInfo, StreamingContext)

 Для правильной обработки исключений необходимо предоставить полный набор конструкторов. Например, конструктор, который имеет сигнатуру `NewException(string, Exception)` используется для создания исключения, вызванные другие исключения. Без этого конструктора не может создать и вызвать экземпляр пользовательского исключения, которое содержит внутреннее исключение (вложенная) — в таком делать какие управляемого кода. Первые три конструктора исключений являются открытыми по соглашению. Четвертый конструктор является защищенным в незапечатанных классов и закрытым в запечатанных классах. Дополнительные сведения см. в разделе [CA2229: Применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте отсутствующий конструктор на исключение и убедитесь, что они имеют правильный уровень доступа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, когда возникает нарушение с помощью другой уровень доступа для открытых конструкторов.

## <a name="example"></a>Пример
 В следующем примере содержится тип исключения, который нарушает это правило и правильно реализованный тип исключения.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]



