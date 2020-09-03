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
ms.openlocfilehash: 1dfd770efd4d690930155d2486b8ff1859065272
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543654"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241. Задайте правильные аргументы для методов форматирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 `format`Строковый аргумент, передаваемый методу <xref:System.Console.WriteLine%2A> , например, <xref:System.Console.Write%2A> или, <xref:System.String.Format%2A?displayProperty=fullName> не содержит элемент форматирования, соответствующий аргументу объекта, или наоборот.

## <a name="rule-description"></a>Описание правила
 Аргументы для таких методов, как <xref:System.Console.WriteLine%2A> , <xref:System.Console.Write%2A> , и <xref:System.String.Format%2A> состоят из строки форматирования, за которой следуют несколько <xref:System.Object?displayProperty=fullName> экземпляров. Строка формата состоит из текста и внедренных элементов форматирования в форме: {index [, Alignment] [: formatString]}. 'index' — это отсчитываемое от нуля целое число, которое указывает форматируемый объект. Если у объекта нет соответствующего индекса в строке формата, объект игнорируется. Если объект, указанный параметром "index", не существует, <xref:System.FormatException?displayProperty=fullName> во время выполнения создается исключение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, укажите элемент форматирования для каждого аргумента объекта и укажите аргумент объекта для каждого элемента форматирования.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показаны два нарушения правила.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
