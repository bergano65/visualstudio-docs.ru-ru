---
title: "Если конструктор действия | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d3928330558c3d611decd2a87498d33fd6482ce
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
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
 [Последовательности](../workflow-designer/sequence-activity-designer.md)   
 [Параллельный](../workflow-designer/parallel-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)