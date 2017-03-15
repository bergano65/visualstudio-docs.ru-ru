---
title: "Конструктор действия TerminateWorkflow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TerminateWorkflow.UI"
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Конструктор действия TerminateWorkflow
Конструктор операций **TerminateWorkflow** используется для создания и настройки действия <xref:System.Activities.Statements.TerminateWorkflow>.  
  
## Действие TerminateWorkflow  
 Действие <xref:System.Activities.Statements.TerminateWorkflow> прерывает выполнение текущего рабочего процесса.  
  
### Использование конструктора операций TerminateWorkflow  
 Конструктор операций **TerminateWorkflow** можно найти в категории **ВыполнениеОбласти элементов**, нажав на вкладку **Область элементов** \(Иначе выберите **Область элементов** из меню **Просмотр**, или же CTRL\+ALT\+X.\)  
  
 Конструктор операций **TerminateWorkflow** можно перетащить из **Области элементов** в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] в любое место, куда обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.TerminateWorkflow> со значением по умолчанию **DisplayName** для TerminateWorkflow.<xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **TerminateWorkflow** либо в поле **DisplayName** таблицы свойств.  
  
### Свойства TerminateWorkflow  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TerminateWorkflow> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Понятное имя действия <xref:System.Activities.Statements.TerminateWorkflow>.Значение по умолчанию — TerminateWorkflow.Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Нет|Исключение, которое будет создано при прерывании рабочего процесса.Задайте это свойство в таблице свойств.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Нет|Причина, которая объясняет причину прерывания рабочего процесса.Задайте это свойство в таблице свойств.|  
  
## См. также  
 [Среда выполнения](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)