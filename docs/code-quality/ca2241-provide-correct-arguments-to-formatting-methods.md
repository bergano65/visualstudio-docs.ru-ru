---
title: "CA2241: предоставьте правильные аргументы методам форматирования | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2241"
  - "Provide correct arguments to formatting methods"
  - "ProvideCorrectArgumentsToFormattingMethods"
helpviewer_keywords: 
  - "CA2241"
  - "ProvideCorrectArgumentsToFormattingMethods"
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2241: предоставьте правильные аргументы методам форматирования
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Строковый аргумент `format`, передаваемый такому методу, как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> и <xref:System.String.Format%2A?displayProperty=fullName>, не содержит элемента форматирования, соответствующего каждому аргументу объекта, или наоборот.  
  
## Описание правила  
 Аргументы методов, таких как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> и <xref:System.String.Format%2A>, состоят из строки формата и нескольких экземпляров <xref:System.Object?displayProperty=fullName>.  Строка формата состоит из текста и внедренных элементов форматирования формы {index\[,alignment\]\[:formatString\]}. 'index' — это отсчитываемое от нуля целое число, которое указывает форматируемый объект.  Если объект не имеет соответствующего индекса в строке формата, этот объект игнорируется.  Если объект, заданный 'index', не существует, во время выполнения создается исключение <xref:System.FormatException?displayProperty=fullName>.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, необходимо предоставить элемент форматирования для каждого аргумента объекта и аргумент объекта для каждого элемента форматирования.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показаны два нарушения данного правила.  
  
 [!CODE [FxCop.Usage.FormattingArguments#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments#1)]