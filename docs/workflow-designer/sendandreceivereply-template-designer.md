---
title: "Конструктор шаблона SendAndReceiveReply | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: be208d526fdc9f1d6f434425e3931b0f0a6510f5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="sendandreceivereply-template-designer"></a>Конструктор шаблона SendAndReceiveReply
**SendAndReceiveReply** шаблон используется для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> действий в <xref:System.Activities.Statements.Sequence> действия, которые соотносятся как часть обмен сообщениями запрос ответ шаблон на стороне клиента.  
  
## <a name="the-sendandreceivereply-template"></a>Шаблон SendAndReceiveReply  
 Добавление **SendAndReceiveReply** шаблона выполняет три операции Помимо создания <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> действий в <xref:System.Activities.Statements.Sequence> действия:  
  
1.  Настраивает свойства <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Send>.  
  
2.  Привязывает свойство <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> действия <xref:System.ServiceModel.Activities.ReceiveReply> к действию <xref:System.ServiceModel.Activities.Send>.  
  
3.  Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.  
  
### <a name="using-the-sendandreceivereply-template-designer"></a>Использование конструктора шаблонов SendAndReceiveReply  
 **SendAndReceiveReply** конструктора действий можно найти в **обмен сообщениями** категории **элементов**, который нажав **элементов**  на вкладке [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **SendAndReceiveReply** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , где обычно размещаются действия. При этом создается <xref:System.ServiceModel.Activities.Send> действия, который может быть настроен с **отправки** конструктора действий и связанное <xref:System.ServiceModel.Activities.ReceiveReply> , можно настроить с помощью **ReceiveReplyForSend** конструктора.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]с помощью **отправки** конструктор для настройки <xref:System.ServiceModel.Activities.Send> действия, в разделе [отправки](../workflow-designer/send-activity-designer.md) раздела.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]с помощью **ReceiveReplyForSend** конструктор для настройки <xref:System.ServiceModel.Activities.ReceiveReply> действие, в следующем разделе.  
  
### <a name="properties-of-receivereply"></a>Свойства ReceiveReply  
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.ReceiveReply> и описано их использование в конструкторе. These properties can be edited in properties grid and some can be edited on [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]designer surface.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.ReceiveReply>. По умолчанию - ReceiveReplyForSend.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|Ссылка на действие <xref:System.ServiceModel.Activities.Send>, связанное с этим действием <xref:System.ServiceModel.Activities.ReceiveReply>. Это свойство не должно быть **null**. Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> используются совместно на клиенте для моделирования обмена сообщениями по принципу «запрос–ответ». Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. Это свойство нельзя изменить в конструкторе, поскольку оно автоматически привязывается к действию <xref:System.ServiceModel.Activities.Send>, из которого было создано действие <xref:System.ServiceModel.Activities.ReceiveReply>.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Это свойство можно изменить, нажав кнопку с многоточием рядом с **содержимого** в таблице свойств или нажав кнопку **определение...**  рядом **содержимого** метки на **Receive** области конструктора операций. Как отобразить **определение содержимого** диалогового окна. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Установите этот флажок, см. в разделе [содержимого диалоговое окно Определение](../workflow-designer/content-definition-dialog-box.md) раздела.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом с <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> свойства в сетке свойств, чтобы открыть **Добавление инициализаторов корреляции** диалоговое окно. [!INCLUDE[crabout](../test/includes/crabout_md.md)]При помощи этого списка в разделе [CorrelationInitializers диалоговое окно Добавление](../workflow-designer/add-correlationinitializers-dialog-box.md) раздела.|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Указывает заголовок действия сообщения. Если значение не задано явным образом, устанавливается значение по умолчанию:<br /><br /> **https://tempuri.org/ {пространство имен контракта службы} / {имя контракта службы} / {имя операции}.**|  
  
## <a name="see-also"></a>См. также  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Получение](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Отправить](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)