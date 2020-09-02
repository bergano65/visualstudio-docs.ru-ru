---
title: Конструкторы действий потока управления | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40f17913864f80e04c3e8b8e703f057094c9bdea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656932"
---
# <a name="control-flow-activity-designers"></a>Конструкторы действия управления потоком
[!INCLUDE[wfd1](../includes/wfd1-md.md)] включает ряд предоставляемых системой действий, которые можно использовать при создании рабочих процессов. В этом разделе содержатся действия, предусмотренные системой, и служащие для управления потоком в пределах рабочего процесса. В следующих подразделах приводится описание этих действий, а также описание их использования.

## <a name="in-this-section"></a>в этом разделе
 [DoWhile](../workflow-designer/dowhile-activity-designer.md) Выполняет действие, содержащееся в его теле по крайней мере один раз, пока заданное условие не примет **значение true**.

 [ForEach \<T> ](foreach-t-activity-designer.md) Выполняет действие, содержащееся в его теле, для каждого элемента в указанной коллекции.

 [Если](../workflow-designer/if-activity-designer.md) Вычисляет условие и выполняет действие в зависимости от результатов этой оценки.

 [Параллельно](../workflow-designer/parallel-activity-designer.md) Выполняет коллекцию дочерних действий одновременно.

 [ParallelForEach \<T> ](../workflow-designer/parallelforeach-t-activity-designer.md) Перечисляет элементы коллекции и выполняет внедренный оператор для каждого элемента коллекции в параллельном режиме

 [Выбор](../workflow-designer/pick-activity-designer.md) Выполняет одну из нескольких ветвей в ответ на событие, предоставляющее управление потоком на основе событий.

 [PickBranch](../workflow-designer/pickbranch-activity-designer.md) Предоставляет потенциальный путь выполнения в рамках <xref:System.Activities.Statements.Pick> действия.

 [Последовательность](../workflow-designer/sequence-activity-designer.md) Содержит упорядоченную коллекцию дочерних действий, выполняемых по порядку.

 [Параметр \<T> ](switch-t-activity-designer.md) Вычисляет указанное выражение и выполняет действие из коллекции действий, связанный ключ которых соответствует значению, полученному в результате вычисления.

 [Во время выполнения](../workflow-designer/while-activity-designer.md) Выполняет действие, содержащееся в его теле, пока заданное условие принимает **значение true**.

## <a name="reference"></a>Справочник
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

 [Обмен сообщениями](../workflow-designer/messaging-activity-designers.md)

 [Параметры выполнения](../workflow-designer/runtime-activity-designers.md)

 [Примитивы](../workflow-designer/primitives-activity-designers.md)

 [Транзакция](../workflow-designer/transaction-activity-designers.md)

 [Коллекция](../workflow-designer/collection-activity-designers.md)

 [Обработка ошибок](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>Внешние ресурсы
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)