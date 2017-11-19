---
title: "Конструктор шаблона ReceiveAndSendReply | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ef7b027eb82b149f3cffcd54c976e1be608c2190
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="receiveandsendreply-template-designer"></a>Конструктор шаблона ReceiveAndSendReply
**ReceiveAndSendReply** шаблон используется для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> действий в <xref:System.Activities.Statements.Sequence> действия, которые соотносятся как часть обмен сообщениями запрос ответ шаблон на сервере.  
  
## <a name="the-receiveandsendreply-template"></a>Шаблон ReceiveAndSendReply  
 Добавление **ReceiveAndSendReply** шаблона выполняет три операции Помимо создания <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> действия с <xref:System.Activities.Statements.Sequence> действия:  
  
1.  Настраивает свойства <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Receive>.  
  
2.  Привязывает свойство <xref:System.ServiceModel.Activities.SendReply.Request%2A> действия <xref:System.ServiceModel.Activities.Receive> к действию <xref:System.ServiceModel.Activities.Send>.  
  
3.  Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.  
  
### <a name="using-the-receiveandsendreply-template-designer"></a>Использование конструктора шаблонов ReceiveAndSendReply  
 **ReceiveAndSendReply** конструктора действий можно найти в **обмен сообщениями** категории **элементов**, который нажав **элементов**  вкладке [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **ReceiveAndSendReply** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , где обычно размещаются действия. При этом создается <xref:System.ServiceModel.Activities.Receive> действия, который может быть настроен с **отправки** конструктора действий и связанное <xref:System.ServiceModel.Activities.SendReply> , можно настроить с помощью конструктора SendReplyToReceive.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]с помощью **Receive** конструктор для настройки <xref:System.ServiceModel.Activities.Receive> действия, в разделе [Receive](../workflow-designer/receive-activity-designer.md) раздела.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]с помощью **SendReplyToReceive** конструктор для настройки <xref:System.ServiceModel.Activities.SendReply> действие, в следующем разделе.  
  
### <a name="properties-of-sendreply"></a>Свойства SendReply  
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.SendReply> и описано их использование в конструкторе. These properties can be edited in properties grid and some can be edited on [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]designer surface.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.SendReply>. По умолчанию используется SendReplyToReceive.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Ссылка на действие <xref:System.ServiceModel.Activities.Receive>, связанное с этим действием <xref:System.ServiceModel.Activities.SendReply>. Это свойство не должно быть **null**. Действия <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> используются на сервере вместе для моделирования обмена сообщениями по шаблону «запрос–ответ». Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. Это свойство нельзя изменить в конструкторе, поскольку оно автоматически привязывается к действию <xref:System.ServiceModel.Activities.Send>, из которого было создано действие <xref:System.ServiceModel.Activities.SendReply>.|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Это свойство можно изменить, нажав кнопку с многоточием рядом с **содержимого** в таблице свойств или нажав кнопку **определение...**  рядом **содержимого** метки на **Receive** области конструктора операций. Как отобразить **определение содержимого** диалогового окна. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Установите этот флажок, см. в разделе [содержимого диалоговое окно Определение](../workflow-designer/content-definition-dialog-box.md) раздела.|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом с <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> свойства в сетке свойств, чтобы открыть **Добавление инициализаторов корреляции** диалоговое окно. [!INCLUDE[crabout](../test/includes/crabout_md.md)]При помощи этого списка в разделе [CorrelationInitializers диалоговое окно Добавление](../workflow-designer/add-correlationinitializers-dialog-box.md) раздела.|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Указывает заголовок действия сообщения. Если значение не задано явным образом, устанавливается значение по умолчанию:<br /><br /> **https://tempuri.org/ {пространство имен контракта службы} / {имя контракта службы} / {имя операции}**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Указывает, нужно ли сохранять экземпляр рабочего процесса до отправки ответного сообщения. Значение по умолчанию — **false**.|  
  
## <a name="see-also"></a>См. также  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Получение](../workflow-designer/receive-activity-designer.md)   
 [Отправить](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)