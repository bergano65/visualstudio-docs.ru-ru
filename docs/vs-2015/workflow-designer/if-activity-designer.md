---
title: Конструктор действий If | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b35fe7f1b55dde25ec896f230f66cef00d24eed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659057"
---
# <a name="if-activity-designer"></a>Конструктор действия If
Действие <xref:System.Activities.Statements.If> оценивает условие и выполняет действие в зависимости от результатов оценки. Данное действие чрезвычайно полезно при использовании процедурного стиля моделирования программирования. Например, действие <xref:System.Activities.Statements.If> может быть вложено в действие <xref:System.Activities.Statements.Sequence> или действие <xref:System.Activities.Statements.Parallel>. При использовании действия <xref:System.Activities.Statements.Flowchart> рассмотрите возможность использования вместо него действия <xref:System.Activities.Statements.FlowDecision>.

## <a name="if-properties-in-the-workflow-designer"></a>Свойства If в конструкторе рабочих процессов
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.If>, которые применяются чаще всего, и описано их использование в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|True|Условие, определяющее, какое дочернее действие следует выполнить. Чтобы задать <xref:System.Activities.Statements.If.Condition%2A>, введите [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выражение в поле **условие** в конструкторе действий **If** или в сетке свойств.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Действие, выполняемое, если <xref:System.Activities.Statements.If.Condition%2A> имеет **значение false**. Чтобы добавить действие, выполняемое <xref:System.Activities.Statements.If.Else%2A> ветви, перетащите действие из **области элементов** в поле **else** в конструкторе действий **If** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.If.Then%2A>|False|Действие, выполняемое, если <xref:System.Activities.Statements.If.Condition%2A> имеет **значение true**. Чтобы добавить действие, выполняемое <xref:System.Activities.Statements.If.Then%2A> ветви, перетащите действие из **области элементов** в поле **затем** в конструкторе действий **If** с текстом подсказки "перетащите действие сюда".|

## <a name="see-also"></a>См. также раздел
 [Поток управления](../workflow-designer/control-flow-activity-designers.md) [параллельной](../workflow-designer/parallel-activity-designer.md) [последовательности](../workflow-designer/sequence-activity-designer.md)