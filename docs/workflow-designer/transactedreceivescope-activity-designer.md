---
title: "Конструктор действия TransactedReceiveScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Конструктор действия TransactedReceiveScope
Конструктор операций  **TransactedReceiveScope** используется для создания и настройки действия <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
## Действие TransactedReceiveScope  
 Действие <xref:System.ServiceModel.Activities.TransactedReceiveScope> позволяет передать транзакцию в состав транзакций сервера, созданных рабочим процессом или диспетчером.  
  
### Использование конструктора операций TransactedReceiveScope  
 Конструктор операций  **TransactedReceiveScope** можно найти в категории **Обмен сообщениямиОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или нажмите CTRL\+ALT\+X\).  
  
 Конструктор операций  **TransactedReceiveScope** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], куда обычно размещаются действия.Будет создано действие <xref:System.ServiceModel.Activities.TransactedReceiveScope> со значением по умолчанию **DisplayName** для TransactedReceiveScope.Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **TransactedReceiveScope** либо в поле **DisplayName** таблицы свойств.  
  
 Конструктор **TransactedReceiveScope** содержит поля **Запрос** и **Тело**.Они используются для настройки свойства <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, задающего действие <xref:System.ServiceModel.Activities.Receive> и свойство <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, которое задает другое действие <xref:System.Activities.Activity>.Свойство <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> создает транзакцию.Затем транзакция определяется как внешняя для области <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, так что любое действие в области выполняется внутри данной транзакции.  
  
### Свойства TransactedReceiveScope  
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.TransactedReceiveScope> и описано их использование в конструкторе.Данное свойство <xref:System.Activities.Activity.DisplayName%2A> может быть изменено в таблице свойств или в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], однако другие свойства можно изменить только в области конструктора.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Дополнительное понятное имя действия <xref:System.ServiceModel.Activities.TransactedReceiveScope>.Значение по умолчанию — TransactedReceiveScope.<br /><br /> Для имени <xref:System.Activities.Activity.DisplayName%2A> нет жестких требований, однако лучше всего использовать отображаемое имя.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Да|Добавляет действие <xref:System.ServiceModel.Activities.Receive> в блок **Запрос** области конструктора операций.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Нет|Добавляет действие <xref:System.Activities.Activity> в блок **Тело** области конструктора операций.|  
  
## См. также  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)