---
title: 'CA2241: Предоставьте правильные аргументы методам форматирования | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8288059b2330d96d9912036b820ec3d3c859752f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171994"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: предоставьте правильные аргументы методам форматирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 `format` Строку аргумент, переданный методу, такие как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, или <xref:System.String.Format%2A?displayProperty=fullName> не содержит элемент форматирования, соответствующий каждому аргументу объекта, или наоборот.

## <a name="rule-description"></a>Описание правила
 Аргументы для методов, таких как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, и <xref:System.String.Format%2A> состоят из строк формата, следуют несколько <xref:System.Object?displayProperty=fullName> экземпляров. Строка формата состоит из текста и внедренного форматирование элементов в формате {индекс [, выравнивание] [: formatString]}. 'index' — это отсчитываемое от нуля целое число, которое указывает форматируемый объект. Если объект не имеет соответствующий индекс в строке формата, объект учитывается. Если объект, указанный «index» не существует, <xref:System.FormatException?displayProperty=fullName> возникает исключение во время выполнения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, предоставляет элемента формата для каждого объекта-аргумента и аргумент объекта для каждого элемента форматирования.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Следующий пример показывает два нарушения данного правила.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]



