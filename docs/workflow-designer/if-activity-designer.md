---
title: Конструктор действий конструктор рабочих процессов-if
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e0c08d655393a953e1abae9d33086d43e281500
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650238"
---
# <a name="if-activity-designer"></a>Конструктор действия If

Действие <xref:System.Activities.Statements.If> оценивает условие и выполняет действие в зависимости от результатов оценки. Данное действие чрезвычайно полезно при использовании процедурного стиля моделирования программирования. Например, действие <xref:System.Activities.Statements.If> может быть вложено в действие <xref:System.Activities.Statements.Sequence> или действие <xref:System.Activities.Statements.Parallel>. При использовании действия <xref:System.Activities.Statements.Flowchart> рассмотрите возможность использования вместо него действия <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Свойства If в конструкторе рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.If>, которые применяются чаще всего, и описано их использование в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|Условие, определяющее, какое дочернее действие следует выполнить. Чтобы задать <xref:System.Activities.Statements.If.Condition%2A>, введите Visual Basic выражение в поле **условие** в конструкторе действий **If** или в сетке свойств.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Действие, выполняемое, если <xref:System.Activities.Statements.If.Condition%2A> имеет **значение false**. Чтобы добавить действие, выполняемое <xref:System.Activities.Statements.If.Else%2A> ветви, перетащите действие из **области элементов** в поле **else** в конструкторе действий **If** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.If.Then%2A>|False|Действие, выполняемое, если <xref:System.Activities.Statements.If.Condition%2A> имеет **значение true**. Чтобы добавить действие, выполняемое <xref:System.Activities.Statements.If.Then%2A> ветви, перетащите действие из **области элементов** в поле **затем** в конструкторе действий **If** с текстом подсказки "перетащите действие сюда".|

## <a name="see-also"></a>См. также

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)