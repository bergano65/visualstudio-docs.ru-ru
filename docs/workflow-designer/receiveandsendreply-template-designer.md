---
title: "Конструктор шаблона ReceiveAndSendReply | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.ReceiveAndSendReply.UI"
  - "System.ServiceModel.Activities.SendReply.UI"
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Конструктор шаблона ReceiveAndSendReply
Шаблон **ReceiveAndSendReply** служит для создания пары предварительно настроенных действий <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> в пределах действия <xref:System.Activities.Statements.Sequence>, которые коррелируются как часть шаблона обмена сообщениями «запрос\-ответ» на сервере.  
  
## Шаблон ReceiveAndSendReply  
 Добавление шаблона **ReceiveAndSendReply** выполняет три операции, помимо создания действий <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> с действием <xref:System.Activities.Statements.Sequence>:  
  
1.  Настраивает свойства <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Receive>.  
  
2.  Привязывает свойство <xref:System.ServiceModel.Activities.SendReply.Request%2A> действия <xref:System.ServiceModel.Activities.Receive> к действию <xref:System.ServiceModel.Activities.Send>.  
  
3.  Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.  
  
### Использование конструктора шаблонов ReceiveAndSendReply  
 Конструктор операций **ReceiveAndSendReply** можно найти в категории **Обмен сообщениямиОбласти элементов**, открыв вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(либо выберите **Область элементов** в меню **Вид** или нажмите CTRL\+ALT\+X\).  
  
 Конструктор операций **ReceiveAndSendReply** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], где обычно размещаются действия.При этом создается действие <xref:System.ServiceModel.Activities.Receive>, которое может быть настроено с помощью конструктора операций **Send** и связанное с ним действие <xref:System.ServiceModel.Activities.SendReply>, которое можно настроить с помощь конструктора SendReplyToReceive.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] использовании конструктора **Receive** для настройки действия <xref:System.ServiceModel.Activities.Receive> см. в разделе [Receive](../workflow-designer/receive-activity-designer.md).  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] использовании конструктора **SendReplyToReceive** для настройки действия <xref:System.ServiceModel.Activities.SendReply> см. в следующем подразделе.  
  
### Свойства SendReply  
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.SendReply> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области конструктора [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Дополнительное понятное имя действия <xref:System.ServiceModel.Activities.SendReply>.По умолчанию используется SendReplyToReceive.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|Да|Ссылка на действие <xref:System.ServiceModel.Activities.Receive>, связанное с этим действием <xref:System.ServiceModel.Activities.SendReply>.Это свойство не должно иметь значение **null**.Действия <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> используются совместно на сервере для моделирования обмена сообщениями по принципу запрос\/ответ.Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>.Это свойство нельзя изменить в конструкторе, поскольку оно автоматически привязывается к действию <xref:System.ServiceModel.Activities.Send>, из которого было создано действие <xref:System.ServiceModel.Activities.SendReply>.|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|Нет|Указывает получаемое содержимое сообщения или параметра.Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>.Измените это свойство, нажав кнопку с многоточием рядом с полем **Содержимое** в таблице свойств или нажав кнопку **Задать…** рядом с меткой **Содержимое** в области конструктора действий **Receive**.Оба действия приведут к отображению диалогового окна **Определение содержимого**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] использовании этого окна, см. в разделе [Диалоговое окно «Определение содержимого»](../workflow-designer/content-definition-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|Нет|Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса.Нажмите кнопку с многоточием рядом со свойством <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> в сетке свойств, чтобы открыть диалоговое окно **Добавление инициализаторов корреляции**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] использовании этого диалогового окна см. в разделе [Диалоговое окно «Добавление инициализаторов корреляции»](../workflow-designer/add-correlationinitializers-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|Нет|Задает заголовок действия сообщения.Если значение не задано явным образом, устанавливается значение по умолчанию:<br /><br /> **https:\/\/tempuri.org\/{пространство имен контракта службы}\/{имя контракта службы}\/{имя операции}**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Указывает, должен ли экземпляр рабочего процесса быть сохранен до отправки ответного сообщения.По умолчанию задано значение **false**.|  
  
## См. также  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)