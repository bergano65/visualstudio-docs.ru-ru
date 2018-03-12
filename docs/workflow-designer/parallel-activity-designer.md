---
title: "Параллельное действие конструктора | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2d40a016631632ace52257d7086d4b1dca87520f
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="parallel-activity-designer"></a>Конструктор действия Parallel
Действие <xref:System.Activities.Statements.Parallel> выполняет коллекцию дочерних действий параллельно.

## <a name="the-parallel-activity"></a>Действие Parallel
 Действие <xref:System.Activities.Statements.Parallel> хранит свои дочерние действия в коллекции <xref:System.Activities.Statements.Parallel.Branches%2A>. Используйте действие <xref:System.Activities.Statements.Parallel> вместо действия <xref:System.Activities.Statements.Sequence>, если некоторые дочерние действия могут перейти в состояние бездействия.

 Действие <xref:System.Activities.Statements.Parallel> имеет свойство <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>, содержащее указанное пользователем выражение [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Действие <xref:System.Activities.Statements.Parallel> вычисляет это свойство после завершения каждого участка кода. Если значение равно **True**, то <xref:System.Activities.Statements.Parallel> действие завершается без выполнения других участков кода. Если <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> не вычисляется **True**, то <xref:System.Activities.Statements.Parallel> завершается после того, все его дочерние действия будут завершены.

### <a name="using-the-parallel-activity-designer"></a>Использование конструктора действия Parallel
 **Параллельных** конструктора действий можно найти в **поток управления** категории **элементов**, который нажав **элементов**вкладка на левой стороне [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **Параллельных** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно помещаются конструкторы, например, внутри **Последовательность** конструктора действий. После перетаскивания на [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], он создает <xref:System.Activities.Statements.Parallel> действия, которое по умолчанию содержит <xref:System.Activities.Activity.DisplayName%2A> из **параллельных**

 Чтобы добавить действие <xref:System.Activities.Statements.Parallel.Branches%2A> коллекцию действия parallel, перетащите какой-либо другой конструктор действия из **элементов** и поместите его на треугольник внутри **параллельных** конструктора действий. Треугольники обрамляют действия, которые содержатся в ветвях. Дополнительные действия можно добавить, применяя эту процедуру повторно. Порядок действия можно изменять с помощью перетаскивания их в **параллельных** конструктора действий.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Свойства действия Parallel в конструкторе рабочих процессов
 В следующей таблице показаны свойства действия Parallel, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию — **параллельных**. Значение можно дополнительно изменить в **свойства** сетки или напрямую в заголовке конструктора действий.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Да|Содержит коллекцию дочерних действий, которые должны быть выполнены.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Вычисляется после завершения какой-либо ветви. Если значение равно **True**, то запланированные ожидающие выполнения ветви отменяются. Если это свойство не задано или равно **False**, действие завершается, если все его дочерние действия будут завершены. Значение по умолчанию — **null**.|

## <a name="see-also"></a>См. также

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)