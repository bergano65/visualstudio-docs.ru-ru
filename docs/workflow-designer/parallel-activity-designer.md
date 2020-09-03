---
title: Конструктор параллельных действий конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f07dd02f682cd5c61d4d17099c1aeb76bb39bf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593165"
---
# <a name="parallel-activity-designer"></a>Конструктор действия Parallel

Действие <xref:System.Activities.Statements.Parallel> выполняет коллекцию дочерних действий параллельно.

## <a name="the-parallel-activity"></a>Действие Parallel

Действие <xref:System.Activities.Statements.Parallel> хранит свои дочерние действия в коллекции <xref:System.Activities.Statements.Parallel.Branches%2A>. Используйте действие <xref:System.Activities.Statements.Parallel> вместо действия <xref:System.Activities.Statements.Sequence>, если некоторые дочерние действия могут перейти в состояние бездействия.

<xref:System.Activities.Statements.Parallel>Действие имеет <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> свойство, которое содержит указанное пользователем Visual Basic выражение. Действие <xref:System.Activities.Statements.Parallel> вычисляет это свойство после завершения каждой ветви кода. Если значение равно **true**, <xref:System.Activities.Statements.Parallel> действие завершается без выполнения других ветвей. Если значение не <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> принимает **значение true**, <xref:System.Activities.Statements.Parallel> действие завершается после завершения всех его дочерних действий.

### <a name="using-the-parallel-activity-designer"></a>Использование конструктора действия Parallel

Доступ к конструктору **параллельных** действий в категории " **поток управления** " **панели элементов**.

Конструктор **параллельных** действий можно перетащить из **панели элементов** в конструктор рабочих процессовную поверхность, где обычно размещаются конструкторы действий, например, внутри конструктора действий **последовательности** . После его удаления в конструктор рабочих процессов создается <xref:System.Activities.Statements.Parallel> действие, которое по умолчанию содержит значение <xref:System.Activities.Activity.DisplayName%2A> **Parallel** .

Чтобы добавить действие в <xref:System.Activities.Statements.Parallel.Branches%2A> коллекцию параллельного действия, перетащите другой конструктор действий из **панели элементов** и поместите его на треугольник в конструкторе **параллельных** действий. Треугольники обрамляют действия, которые содержатся в ветвях. Дополнительные действия можно добавить, применяя эту процедуру повторно. Порядок действий можно изменить, перетащив их в конструктор **параллельных** действий.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Свойства действия Parallel в конструкторе рабочих процессов

В следующей таблице показаны свойства действия Parallel, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию — **Parallel**. Значение можно дополнительно изменить в сетке **свойств** или непосредственно в заголовке конструктора операций.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Верно|Содержит коллекцию дочерних действий, которые должны быть выполнены.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Неверно|Вычисляется после завершения какой-либо ветви. Если значение равно **true**, то запланированные ожидающие ветви отменяются. Если это свойство не задано или имеет **значение false**, действие завершается после завершения всех его дочерних действий. Значение по умолчанию — **null**.|

## <a name="see-also"></a>См. также раздел

- [Последовательность](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
