---
title: "Конструктор шаблона SendAndReceiveReply | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.SendAndReceiveReply.UI"
  - "System.ServiceModel.Activities.ReceiveReply.UI"
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Конструктор шаблона SendAndReceiveReply
Шаблон  **SendAndReceiveReply** используется для создания пары предварительно настроенных действий <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> в пределах действия <xref:System.Activities.Statements.Sequence>, которые соотносятся как часть шаблона обмена сообщениями запроса\/ответа на клиенте.  
  
## Шаблон SendAndReceiveReply  
 Добавление шаблона  **SendAndReceiveReply** выполняет три операции помимо создания действий <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> в пределах действия <xref:System.Activities.Statements.Sequence>.  
  
1.  Настраивает свойства <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Send>.  
  
2.  Привязывает свойство <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> действия <xref:System.ServiceModel.Activities.ReceiveReply> к действию <xref:System.ServiceModel.Activities.Send>.  
  
3.  Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.  
  
### Использование конструктора шаблонов SendAndReceiveReply  
 Конструктор операций  **SendAndReceiveReply** можно найти в категории **Обмен сообщениямиОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или нажмите CTRL\+ALT\+X\).  
  
 Конструктор операций  **SendAndReceiveReply** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], куда обычно размещаются действия.При этом создается действие <xref:System.ServiceModel.Activities.Send>, которое может быть настроено с помощью конструктора операций **Send** и связанным <xref:System.ServiceModel.Activities.ReceiveReply>, которое может быть настроено с помощь конструктора **ReceiveReplyForSend**.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] Сведения об использовании конструктора  **Send** для настройки действия <xref:System.ServiceModel.Activities.Send> см. в разделе [Send](../workflow-designer/send-activity-designer.md).  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] Сведения об использовании конструктора  **ReceiveReplyForSend** для настройки действия <xref:System.ServiceModel.Activities.ReceiveReply> см. в следующем разделе.  
  
### Свойства ReceiveReply  
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.ReceiveReply> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области конструктора [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Дополнительное понятное имя действия <xref:System.ServiceModel.Activities.ReceiveReply>.По умолчанию — ReceiveReplyForSend.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|Да|Ссылка на действие <xref:System.ServiceModel.Activities.Send>, связанное с этим действием <xref:System.ServiceModel.Activities.ReceiveReply>.Это свойство не должно иметь значение **null**.Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> используются совместно на клиенте для моделирования обмена сообщениями по принципу запрос\/ответ.Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>.Это свойство нельзя изменить в конструкторе, поскольку оно автоматически привязывается к действию <xref:System.ServiceModel.Activities.Send>, из которого было создано действие <xref:System.ServiceModel.Activities.ReceiveReply>.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|Нет|Указывает получаемое содержимое сообщения или параметра.Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>.Измените это свойство, нажав кнопку с многоточием рядом с полем **Содержимое** в таблице свойств или нажав кнопку **Задать…** рядом с меткой **Содержимое** в области конструктора действий **Receive**.Оба действия приведут к отображению диалогового окна **Определение содержимого**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] использовании этого окна см. в разделе [Диалоговое окно «Определение содержимого»](../workflow-designer/content-definition-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|Нет|Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса.Нажмите кнопку с многоточием рядом со свойством <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> в сетке свойств, чтобы открыть диалоговое окно **Добавление инициализаторов корреляции**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] использовании этого диалогового окна см. в разделе [Диалоговое окно «Добавление инициализаторов корреляции»](../workflow-designer/add-correlationinitializers-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|Нет|Задает заголовок действия сообщения.Если значение не задано явным образом, устанавливается значение по умолчанию:<br /><br /> **https:\/\/tempuri.org\/{пространство имен контракта службы}\/{имя контракта службы}\/{имя операции}.**|  
  
## См. также  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)