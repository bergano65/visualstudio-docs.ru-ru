---
title: "Конструктор действия TransactionScope | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TransactionScope.UI"
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия TransactionScope
Конструктор операций  **TransactionScope** используется для создания и настройки действия <xref:System.Activities.Statements.TransactionScope>.  
  
## Действие TransactionScope  
 Действие <xref:System.Activities.Statements.TransactionScope> выполняет вложенное действие за одну транзакцию.Транзакция фиксируется, после того как действие <xref:System.Activities.Statements.TransactionScope.Body%2A> и все другие участники транзакции успешно завершаются.  
  
### Использование конструктора операций TransactionScope  
 Конструктор операций  **TransactionScope** можно найти в категории **ТранзакцияОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или нажмите CTRL\+ALT\+X\).  
  
 Конструктор операций  **TransactionScope** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], куда обычно размещаются действия, например, внутри <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.TransactionScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для TransactionScope.Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций  **TransactionScope** либо в поле **DisplayName** сетки свойств.  
  
### Свойства TransactionScope  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TransactionScope> и описано их использование в конструкторе.Свойства <xref:System.Activities.Activity.DisplayName%2A> и <xref:System.Activities.Statements.TransactionScope.Body%2A> можно изменить в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Но другие свойства следует изменять в таблице свойств.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Дополнительное понятное имя действия <xref:System.Activities.Statements.TransactionScope>.По умолчанию выбрано значение TransactionScope.Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Да|Указывает действие, которое следует выполнить за одну транзакцию.Чтобы добавить действие <xref:System.Activities.Statements.TransactionScope.Body%2A>, перетащите его из **Панели инструментов** в поле **Текст** на конструкторе операций  **TransactionScope** с текстом подсказки указания действие сюда».|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Задает <xref:System.Transactions.IsolationLevel> для объекта <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Задает интервал времени \(в формате 00:00:00, что означает часы:минуты:секунды\), в течение которого транзакция должна завершиться.Значение по умолчанию — 1 минута \(00:01:00\).|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>|True|Задает значение, которое указывает, следует ли прерывать рабочий процесс, если прервана транзакция.|  
  
## См. также  
 [Транзакция](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)