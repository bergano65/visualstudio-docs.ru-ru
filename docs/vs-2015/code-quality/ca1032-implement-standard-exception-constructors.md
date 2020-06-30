---
title: 'CA1032: реализуйте стандартные конструкторы исключений | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 61b0157200ddff4cb8335118b30832a0c8950f65
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542289"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032. Реализуйте стандартные конструкторы исключений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип расширяет <xref:System.Exception?displayProperty=fullName> и не объявляет все необходимые конструкторы.

## <a name="rule-description"></a>Описание правила
 Типы исключений должны реализовывать следующие конструкторы:

- общедоступная Невексцептион ()

- Public Невексцептион (строка)

- Public Невексцептион (строка, исключение)

- protected или Private Невексцептион (SerializationInfo, StreamingContext)

  Для правильной обработки исключений необходимо предоставить полный набор конструкторов. Например, конструктор с сигнатурой `NewException(string, Exception)` используется для создания исключений, вызванных другими исключениями. Без этого конструктора нельзя создать и вызвать экземпляр пользовательского исключения, содержащего внутреннее (вложенное) исключение, которое в таком случае должно делать управляемый код. Первые три конструктора исключений являются общедоступными по соглашению. Четвертый конструктор защищен в незапечатанных классах и закрыт в запечатанных классах. Дополнительные сведения см. в разделе [CA2229: реализация конструкторов сериализации.](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте недостающие конструкторы в исключение и убедитесь, что они имеют правильную доступность.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 В этом правиле можно отключить вывод предупреждений, если нарушение вызвано использованием другого уровня доступа для открытых конструкторов.

## <a name="example"></a>Пример
 В следующем примере содержится тип исключения, нарушающий это правило, и тип исключения, который был правильно реализован.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
