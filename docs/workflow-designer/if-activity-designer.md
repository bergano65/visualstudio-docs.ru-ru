---
title: "Конструктор действия If | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.If.UI"
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Конструктор действия If
Действие <xref:System.Activities.Statements.If> оценивает условие и выполняет действие в зависимости от результатов оценки.Данное действие чрезвычайно полезно при использовании процедурного стиля моделирования программирования.Например, действие <xref:System.Activities.Statements.If> может быть вложено в действие <xref:System.Activities.Statements.Sequence> или действие <xref:System.Activities.Statements.Parallel>.При использовании действия <xref:System.Activities.Statements.Flowchart> рассмотрите возможность использования вместо него действия <xref:System.Activities.Statements.FlowDecision>.  
  
## Свойства If в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.If>, которые применяются чаще всего, и описано их использование в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Statements.If.Condition%2A>|Да|Условие, определяющее, какое дочернее действие следует выполнить.Для установки <xref:System.Activities.Statements.If.Condition%2A> введите выражение [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] в поле **Условие** конструктора операций **If** или в таблицу свойств.|  
|<xref:System.Activities.Statements.If.Else%2A>|Нет|Действие, выполняемое в случае, если <xref:System.Activities.Statements.If.Condition%2A> принимает значение **false**.Чтобы добавить действие, выполняемое ветвью <xref:System.Activities.Statements.If.Else%2A>, перетащите его из **Области элементов** в поле **Else** на конструкторе операций **If** с текстом подсказки «Перетащить действие сюда».|  
|<xref:System.Activities.Statements.If.Then%2A>|Нет|Действие, выполняемое в случае, если условие <xref:System.Activities.Statements.If.Condition%2A> принимает значение **true**.Чтобы добавить действие, выполняемое ветвью <xref:System.Activities.Statements.If.Then%2A>, перетащите его из **Области элементов** в поле **Then** на конструкторе операций **If** с текстом подсказки «Перетащить действие сюда».|  
  
## См. также  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Управление потоком](../workflow-designer/control-flow-activity-designers.md)