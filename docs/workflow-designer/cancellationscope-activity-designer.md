---
title: "Конструктор действия CancellationScope | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CancellationScope.UI"
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия CancellationScope
Конструктор операций **CancellationScope** используется для создания и настройки действия <xref:System.Activities.Statements.CancellationScope>.  
  
## Действие CancellationScope  
 Действие <xref:System.Activities.Statements.CancellationScope> позволяет указать действие Ю, позволяющее логически разрешить или запретить выполнение этого действия.  
  
### Использование конструктора операций CancellationScope  
 Конструктор операций **CancellationScope** можно найти в категории **ТранзакцииОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или же CTRL\+ALT\+X.\)  
  
 Конструктор операций **CancellationScope** можно перетащить из **Области элементов** в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] в любое место, куда обычно размещаются действия, например, внутри <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.CancellationScope> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для CancellationScope.Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **CancellationScope** либо в поле **DisplayName** таблицы свойств.  
  
### Свойства CancellationScope  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.CancellationScope> и описано их использование в конструкторе.Свойство <xref:System.Activities.Activity.DisplayName%2A> можно изменить в таблице свойств, но другие свойства должны изменяться в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] области.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Дополнительное понятное имя действия <xref:System.Activities.Statements.CancellationScope>.По умолчанию — CancellationScope.Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Да|Указывает действие, для которого предусмотрена отменяющая логика.Чтобы добавить действие <xref:System.Activities.Statements.CancellationScope.Body%2A>, перетащите его из **Панели элементов** в поле **Тело** на конструкторе операций **CancellationScope** с текстом подсказки «Перетащить действие сюда».|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Да|Указывает действие, выполняемое в случае отмены.Чтобы добавить действие <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, перетащите действие из **Области элементов** в окно **CancellationHandler** в конструкторе действий **CancellationScope** с текстом подсказки «Перетащить действие сюда».|  
  
## См. также  
 [Транзакция](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)