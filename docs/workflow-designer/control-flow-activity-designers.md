---
title: "Конструкторы действия управления потоком | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Конструкторы действия управления потоком
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] включает определенное количество системных действий, которые могут быть использованы для построения рабочих процессов.В этом разделе содержатся действия, предусмотренные системой, и служащие для управления потоком в пределах рабочего процесса.В следующих подразделах приводится описание этих действий, а также описание их использования.  
  
## В этом подразделе  
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)  
 Выполняет действие, содержащееся в теле хотя бы один раз, до тех пор, пока результатом вычисления указанного условия не станет **true**.  
  
 [ForEach\<T\>](http://msdn.microsoft.com/ru-ru/a680cddd-2760-497a-b27b-c023fcbc6f33)  
 Выполняет действие, содержащееся в теле, для каждого элемента в указанной коллекции.  
  
 [If](../workflow-designer/if-activity-designer.md)  
 Проверяет условие и выполняет действие в зависимости от результата вычисления.  
  
 [Parallel](../workflow-designer/parallel-activity-designer.md)  
 Одновременно выполняет коллекцию вложенных действий.  
  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)  
 Перечисляет элементы коллекции и выполняет встроенный оператор для каждого элемента коллекции параллельно.  
  
 [Pick](../workflow-designer/pick-activity-designer.md)  
 Выполняет одну из нескольких ветвей по некоторому событию, которое обеспечивает управление потоком на основе событий.  
  
 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)  
 Представляет потенциальный путь выполнения в действии <xref:System.Activities.Statements.Pick>.  
  
 [Sequence](../workflow-designer/sequence-activity-designer.md)  
 Содержит упорядоченную коллекцию вложенных действий, которые выполняются последовательно.  
  
 [Switch\<T\>](http://msdn.microsoft.com/ru-ru/ce1aa634-c4db-4475-a1c8-a88478a57212)  
 Вычисляет заданное выражение и выполняет действие из коллекции действий, связанный ключ которого соответствует значению, полученному в результате вычисления.  
  
 [While](../workflow-designer/while-activity-designer.md)  
 Выполняет действие, содержащееся в тексте, до тех пор, пока указанное условие вычисляется для **true**.  
  
## Ссылка  
 <xref:System.Activities.Activity>  
  
 <xref:System.Activities.Statements.DoWhile>  
  
 <xref:System.Activities.Statements.ForEach%601>  
  
 <xref:System.Activities.Statements.If>  
  
 <xref:System.Activities.Statements.Parallel>  
  
 <xref:System.Activities.Statements.ParallelForEach%601>  
  
 <xref:System.Activities.Statements.Pick>  
  
 <xref:System.Activities.Statements.PickBranch>  
  
 <xref:System.Activities.Statements.Sequence>  
  
 <xref:System.Activities.Statements.Switch%601>  
  
 <xref:System.Activities.Statements.While>  
  
## Связанные подразделы  
 Сведения о других типах конструкторов действий см. в следующих подразделах.  
  
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)  
  
 [Блок\-схема](../workflow-designer/flowchart-activity-designers.md)  
  
 [Обмен сообщениями](../workflow-designer/messaging-activity-designers.md)  
  
 [Среда выполнения](../workflow-designer/runtime-activity-designers.md)  
  
 [Базовые функции](../workflow-designer/primitives-activity-designers.md)  
  
 [Транзакция](../workflow-designer/transaction-activity-designers.md)  
  
 [Коллекция](../workflow-designer/collection-activity-designers.md)  
  
 [Обработка ошибок](../workflow-designer/error-handling-activity-designers.md)  
  
## Внешние ресурсы  
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)