---
title: 'CA2241: укажите правильные аргументы для методов форматирования | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 112065b2a8b9a88241ce62dda7b32a2f2c22fc75
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672027"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: предоставьте правильные аргументы методам форматирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 @No__t_0 строковый аргумент, передаваемый методу, например <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> или <xref:System.String.Format%2A?displayProperty=fullName>, не содержит элемент форматирования, соответствующий аргументу объекта, или наоборот.

## <a name="rule-description"></a>Описание правила
 Аргументы для методов, таких как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> и <xref:System.String.Format%2A>, состоят из строки формата, за которой следуют несколько экземпляров <xref:System.Object?displayProperty=fullName>. Строка формата состоит из текста и внедренных элементов форматирования в форме: {index [, Alignment] [: formatString]}. 'index' — это отсчитываемое от нуля целое число, которое указывает форматируемый объект. Если у объекта нет соответствующего индекса в строке формата, объект игнорируется. Если объект, указанный параметром "index", не существует, во время выполнения создается исключение <xref:System.FormatException?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, укажите элемент форматирования для каждого аргумента объекта и укажите аргумент объекта для каждого элемента форматирования.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показаны два нарушения правила.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
