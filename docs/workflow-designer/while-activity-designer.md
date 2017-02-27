---
title: "Конструктор действия While | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.While.UI"
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Конструктор действия While
Действие <xref:System.Activities.Statements.While> выполняет действие, которое содержится в его <xref:System.Activities.Statements.While.Body%2A>, пока результат вычисления указанного <xref:System.Activities.Statements.Condition%2A> равен **true**.Вложенное действие может быть не выполнено ни разу.Если вложенное действие должно быть выполнено хотя бы один раз, пользуйтесь вместо этого действием <xref:System.Activities.Statements.DoWhile>.  
  
## Свойства While в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.While>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.While> в заголовке.Значение по умолчанию — While.Это значение можно изменить в окне **Свойства** или напрямую в заголовке конструктора действий.<br /><br /> Несмотря на то, что значения <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.While.Body%2A>|Нет|Содержит действие, которое выполняется, пока результат вычисления <xref:System.Activities.Statements.Condition%2A> равен **true**.|  
|<xref:System.Activities.Statements.Condition%2A>|Да|Содержит выражение [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], значение которого определяет, будет ли выполнено действие в <xref:System.Activities.Statements.While.Body%2A>.|  
  
## См. также  
 [Управление потоком](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)