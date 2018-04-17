---
title: Если конструктор действия | Документы Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 948359e0c6458fb0ad03d0d032676439d8062ca4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="if-activity-designer"></a>Конструктор действия If
Действие <xref:System.Activities.Statements.If> оценивает условие и выполняет действие в зависимости от результатов оценки. Данное действие чрезвычайно полезно при использовании процедурного стиля моделирования программирования. Например, действие <xref:System.Activities.Statements.If> может быть вложено в действие <xref:System.Activities.Statements.Sequence> или действие <xref:System.Activities.Statements.Parallel>. При использовании действия <xref:System.Activities.Statements.Flowchart> рассмотрите возможность использования вместо него действия <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Свойства If в конструкторе рабочих процессов
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.If>, которые применяются чаще всего, и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|True|Условие, определяющее, какое дочернее действие следует выполнить. Для задания <xref:System.Activities.Statements.If.Condition%2A>, введите команду [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] выражения в **условие** поле на **Если** действие конструктора или в сетке свойств.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Действие, выполняемое, если <xref:System.Activities.Statements.If.Condition%2A> — **false**. Чтобы добавить действие, выполняемое <xref:System.Activities.Statements.If.Else%2A> ветви, перетащите его из **элементов** в **Else** поле на **Если** конструктора действий с текстом подсказки» Перетащить действие сюда».|
|<xref:System.Activities.Statements.If.Then%2A>|False|Действие, выполняемое, если <xref:System.Activities.Statements.If.Condition%2A> — **true**. Чтобы добавить действие, выполняемое <xref:System.Activities.Statements.If.Then%2A> ветви, перетащите его из **элементов** в **затем** поле на **Если** конструктора действий с текстом подсказки» Перетащить действие сюда».|

## <a name="see-also"></a>См. также

- [последовательности](../workflow-designer/sequence-activity-designer.md)
- [Параллельный](../workflow-designer/parallel-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)