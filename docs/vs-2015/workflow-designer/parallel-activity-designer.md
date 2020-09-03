---
title: Конструктор параллельных действий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a46a340ccdeacacb8f04b962313db18975447a67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672639"
---
# <a name="parallel-activity-designer"></a>Конструктор действия Parallel
Действие <xref:System.Activities.Statements.Parallel> выполняет коллекцию дочерних действий параллельно.

## <a name="the-parallel-activity"></a>Действие Parallel
 Действие <xref:System.Activities.Statements.Parallel> хранит свои дочерние действия в коллекции <xref:System.Activities.Statements.Parallel.Branches%2A>. Используйте действие <xref:System.Activities.Statements.Parallel> вместо действия <xref:System.Activities.Statements.Sequence>, если некоторые дочерние действия могут перейти в состояние бездействия.

 Действие <xref:System.Activities.Statements.Parallel> имеет свойство <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>, содержащее указанное пользователем выражение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Действие <xref:System.Activities.Statements.Parallel> вычисляет это свойство после завершения каждой ветви кода. Если значение равно **true**, <xref:System.Activities.Statements.Parallel> действие завершается без выполнения других ветвей. Если значение не <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> принимает **значение true**, <xref:System.Activities.Statements.Parallel> действие завершается после завершения всех его дочерних действий.

### <a name="using-the-parallel-activity-designer"></a>Использование конструктора действия Parallel
 Конструктор **параллельных** операций можно найти в категории **поток управления** **панели элементов**, щелкнув вкладку **область элементов** в левой части окна [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать пункт **панель инструментов** в меню **вид** или CTRL + ALT + X).

 Конструктор **параллельных** операций можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где бы они ни находились, как обычно размещаются конструкторы действий, например внутри конструктора действий **последовательности** . После его удаления в [!INCLUDE[wfd2](../includes/wfd2-md.md)] создается <xref:System.Activities.Statements.Parallel> действие, которое по умолчанию содержит значение <xref:System.Activities.Activity.DisplayName%2A> **Parallel** .

 Чтобы добавить действие в <xref:System.Activities.Statements.Parallel.Branches%2A> коллекцию параллельного действия, перетащите другой конструктор действий из **панели элементов** и поместите его на треугольник в конструкторе **параллельных** действий. Треугольники обрамляют действия, которые содержатся в ветвях. Дополнительные действия можно добавить, применяя эту процедуру повторно. Порядок действий можно изменить, перетащив их в конструктор **параллельных** действий.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Свойства действия Parallel в конструкторе рабочих процессов
 В следующей таблице показаны свойства действия Parallel, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию — **Parallel**. Значение можно дополнительно изменить в сетке **свойств** или непосредственно в заголовке конструктора операций.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Верно|Содержит коллекцию дочерних действий, которые должны быть выполнены.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Неверно|Вычисляется после завершения какой-либо ветви. Если значение равно **true**, то запланированные ожидающие ветви отменяются. Если это свойство не задано или имеет **значение false**, действие завершается после завершения всех его дочерних действий. Значение по умолчанию — **null**.|

## <a name="see-also"></a>См. также:
 [Поток управления](../workflow-designer/control-flow-activity-designers.md) [ParallelForEach \<T> ](../workflow-designer/parallelforeach-t-activity-designer.md) [последовательности](../workflow-designer/sequence-activity-designer.md)