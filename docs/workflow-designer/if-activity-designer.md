---
title: Конструктор действий конструктор рабочих процессов-if
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 099be38c5585fe19c00b31c00ac3a7ddcd3d7fe2
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111464"
---
# <a name="if-activity-designer"></a>Конструктор действия If

Действие <xref:System.Activities.Statements.If> оценивает условие и выполняет действие в зависимости от результатов оценки. Данное действие чрезвычайно полезно при использовании процедурного стиля моделирования программирования. Например, действие <xref:System.Activities.Statements.If> может быть вложено в действие <xref:System.Activities.Statements.Sequence> или действие <xref:System.Activities.Statements.Parallel>. При использовании действия <xref:System.Activities.Statements.Flowchart> рассмотрите возможность использования вместо него действия <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Свойства If в конструкторе рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.If>, которые применяются чаще всего, и описано их использование в конструкторе.

|Имя свойства|Обязательное|Метрики|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Да|Условие, определяющее, какое дочернее действие следует выполнить. Чтобы задать <xref:System.Activities.Statements.If.Condition%2A>, введите Visual Basic выражение в поле **условие** в конструкторе действий **If** или в сетке свойств.|
|<xref:System.Activities.Statements.If.Else%2A>|Ложь|Действие, выполняемое, если <xref:System.Activities.Statements.If.Condition%2A> имеет **значение false**. Чтобы добавить действие, выполняемое <xref:System.Activities.Statements.If.Else%2A> ветви, перетащите действие из **области элементов** в поле **else** в конструкторе действий **If** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.If.Then%2A>|Ложь|Действие, выполняемое, если <xref:System.Activities.Statements.If.Condition%2A> имеет **значение true**. Чтобы добавить действие, выполняемое <xref:System.Activities.Statements.If.Then%2A> ветви, перетащите действие из **области элементов** в поле **затем** в конструкторе действий **If** с текстом подсказки "перетащите действие сюда".|

## <a name="see-also"></a>См. также:

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
