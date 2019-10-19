---
title: Конструктор параллельных действий конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0c1ea74c1cf64252bdae201e8cc3dd529adb7cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650108"
---
# <a name="parallel-activity-designer"></a>Конструктор действия Parallel

Действие <xref:System.Activities.Statements.Parallel> выполняет коллекцию дочерних действий параллельно.

## <a name="the-parallel-activity"></a>Действие Parallel

Действие <xref:System.Activities.Statements.Parallel> хранит свои дочерние действия в коллекции <xref:System.Activities.Statements.Parallel.Branches%2A>. Используйте действие <xref:System.Activities.Statements.Parallel> вместо действия <xref:System.Activities.Statements.Sequence>, если некоторые дочерние действия могут перейти в состояние бездействия.

Действие <xref:System.Activities.Statements.Parallel> имеет свойство <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>, которое содержит указанное пользователем Visual Basic выражение. Действие <xref:System.Activities.Statements.Parallel> вычисляет это свойство после завершения каждой ветви кода. Если значение равно **true**, то действие <xref:System.Activities.Statements.Parallel> завершается без выполнения других ветвей. Если <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> не принимает **значение true**, действие <xref:System.Activities.Statements.Parallel> завершается после завершения всех его дочерних действий.

### <a name="using-the-parallel-activity-designer"></a>Использование конструктора действия Parallel

Доступ к конструктору **параллельных** действий в категории " **поток управления** " **панели элементов**.

Конструктор **параллельных** действий можно перетащить из **панели элементов** в конструктор рабочих процессовную поверхность, где обычно размещаются конструкторы действий, например, внутри конструктора действий **последовательности** . После его удаления в конструктор рабочих процессов создается действие <xref:System.Activities.Statements.Parallel>, которое по умолчанию содержит <xref:System.Activities.Activity.DisplayName%2A> **Parallel** .

Чтобы добавить действие в коллекцию <xref:System.Activities.Statements.Parallel.Branches%2A> параллельного действия, перетащите другой конструктор действий из **панели элементов** и поместите его на треугольник в конструкторе **параллельных** действий. Треугольники обрамляют действия, которые содержатся в ветвях. Дополнительные действия можно добавить, применяя эту процедуру повторно. Порядок действий можно изменить, перетащив их в конструктор **параллельных** действий.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Свойства действия Parallel в конструкторе рабочих процессов

В следующей таблице показаны свойства действия Parallel, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию — **Parallel**. Значение можно дополнительно изменить в сетке **свойств** или непосредственно в заголовке конструктора операций.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Содержит коллекцию дочерних действий, которые должны быть выполнены.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Вычисляется после завершения какой-либо ветви. Если значение равно **true**, то запланированные ожидающие ветви отменяются. Если это свойство не задано или имеет **значение false**, действие завершается после завершения всех его дочерних действий. Значение по умолчанию — **null**.|

## <a name="see-also"></a>См. также

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)