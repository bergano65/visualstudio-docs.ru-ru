---
title: "Конструктор действия Confirm | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Confirm.UI"
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Конструктор действия Confirm
Конструктор действия **Confirm** служит для создания и настройки действия <xref:System.Activities.Statements.Confirm>.  
  
## Действие Confirm  
 Действие <xref:System.Activities.Statements.Confirm> вызывает явным образом обработчик <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> для действия, содержащегося в <xref:System.Activities.Statements.CompensableActivity>.Если действие <xref:System.Activities.Statements.Confirm> не используется в рамках <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> или <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> действия <xref:System.Activities.Statements.CompensableActivity>, то необходимо указать свойство<xref:System.Activities.Statements.Confirm.Target%2A>.  
  
 Объект <xref:System.Activities.Statements.CompensationToken>, указанный <xref:System.Activities.Statements.Compensate.Target%2A>, предоставляет возможность для явного подтверждения или компенсации действия <xref:System.Activities.Statements.CompensableActivity>, как только <xref:System.Activities.Statements.CompensableActivity.Body%2A> действия <xref:System.Activities.Statements.CompensableActivity> будет успешно завершено.  
  
### Использование конструктора действия Confirm  
 Конструктор действия **Confirm** можно найти в категории **ТранзакцияОбласти элементов**, открыв вкладку **Область элементов** в левой части [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(либо выберите **Область элементов** в меню **Вид** или нажмите CTRL\+ALT\+X.\)  
  
 Конструктор действия **Confirm** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], где обычно размещаются действия, например внутрь <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.Confirm>, где значение <xref:System.Activities.Activity.DisplayName%2A> по умолчанию равно Confirm.<xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действия **Confirm** или в поле **DisplayName** таблицы свойств.  
  
### Свойства Confirm  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Confirm> и описано их использование в конструкторе.Свойство <xref:System.Activities.Activity.DisplayName%2A> может быть изменено в таблице свойств или в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], однако свойство <xref:System.Activities.Statements.Confirm.Target%2A> можно изменить только в таблице свойств.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает дополнительное понятное имя действия <xref:System.Activities.Statements.CancellationScope>.По умолчанию используется Confirm.|  
|<xref:System.Activities.Statements.Confirm.Target%2A>|Да|Указывает <xref:System.Activities.InArgument%601>, в котором содержится <xref:System.Activities.Statements.CompensationToken> для данного действия <xref:System.Activities.Statements.Confirm>.|  
  
## См. также  
 [Транзакция](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)