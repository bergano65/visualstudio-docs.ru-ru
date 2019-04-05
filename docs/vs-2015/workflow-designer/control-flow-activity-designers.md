---
title: Конструкторы действий потока управления | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 25f8db1f6d14692538fe7f61ed2f9dbd37e0bd29
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002774"
---
# <a name="control-flow-activity-designers"></a>Конструкторы действия управления потоком
[!INCLUDE[wfd1](../includes/wfd1-md.md)] включает определенное количество системных действий, которые могут быть использованы для построения рабочих процессов. В этом разделе содержатся действия, предусмотренные системой, и служащие для управления потоком в пределах рабочего процесса. В следующих подразделах приводится описание этих действий, а также описание их использования.  
  
## <a name="in-this-section"></a>В этом разделе  
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)  
 Выполняет действие, содержащееся в теле хотя бы один раз, пока заданное условие не примет значение **true**.  
  
 [ForEach\<T>](foreach-t-activity-designer.md)  
 Выполняет действие, содержащееся в теле, для каждого элемента в указанной коллекции.  
  
 [If](../workflow-designer/if-activity-designer.md)  
 Проверяет условие и выполняет действие в зависимости от результата вычисления.  
  
 [Parallel](../workflow-designer/parallel-activity-designer.md)  
 Одновременно выполняет коллекцию вложенных действий.  
  
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)  
 Перечисляет элементы коллекции и выполняет встроенный оператор для каждого элемента коллекции параллельно.  
  
 [Pick](../workflow-designer/pick-activity-designer.md)  
 Выполняет одну из нескольких ветвей по некоторому событию, которое обеспечивает управление потоком на основе событий.  
  
 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)  
 Представляет потенциальный путь выполнения в действии <xref:System.Activities.Statements.Pick>.  
  
 [Sequence](../workflow-designer/sequence-activity-designer.md)  
 Содержит упорядоченную коллекцию вложенных действий, которые выполняются последовательно.  
  
 [Switch\<T>](switch-t-activity-designer.md)  
 Вычисляет заданное выражение и выполняет действие из коллекции действий, связанный ключ которого соответствует значению, полученному в результате вычисления.  
  
 [While](../workflow-designer/while-activity-designer.md)  
 Выполняет действие, содержащееся в его тексте, пока заданное условие, результатом которого является **true**.  
  
## <a name="reference"></a>Ссылка  
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
  
## <a name="related-sections"></a>Связанные разделы  
 Сведения о других типах конструкторов действий см. в следующих подразделах.  
  
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)  
  
 [Блок-схема](../workflow-designer/flowchart-activity-designers.md)  
  
 [Messaging](../workflow-designer/messaging-activity-designers.md)  
  
 [Среда выполнения](../workflow-designer/runtime-activity-designers.md)  
  
 [Примитивы](../workflow-designer/primitives-activity-designers.md)  
  
 [Транзакция](../workflow-designer/transaction-activity-designers.md)  
  
 [Коллекция](../workflow-designer/collection-activity-designers.md)  
  
 [Обработка ошибок](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>Внешние ресурсы  
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)