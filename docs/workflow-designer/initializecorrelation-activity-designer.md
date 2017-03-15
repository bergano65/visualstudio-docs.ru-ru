---
title: "Конструктор действия InitializeCorrelation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.InitializeCorrelation.UI"
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Конструктор действия InitializeCorrelation
Конструктор операций **InitializeCorrelation** используется для создания и настройки действия <xref:System.ServiceModel.Activities.InitializeCorrelation>, который используется для соотнесения сообщений перед их отправкой или получением.  
  
## Действие InitializeCorrelation  
 Действие <xref:System.ServiceModel.Activities.InitializeCorrelation> используется для инициализации соотношений без отправки или получения сообщений.Обычно корреляция инициализируется при отправке или получении сообщения.Если корреляция должна быть установлена до отправки или получения сообщения, то для этого можно использовать <xref:System.ServiceModel.Activities.InitializeCorrelation>.  
  
### Использование конструктора действий InitializeCorrelation  
 Конструктор операций **InitializeCorrelation** можно найти в категории **Обмен сообщениямиОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или же CTRL\+ALT\+X.\)  
  
 Конструктор **InitializeCorrelation** можно перетащить из **Области элементов** и поместить в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Будет создано действие <xref:System.ServiceModel.Activities.InitializeCorrelation> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для InitializeCorrelation.Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **InitializeCorrelation** либо в поле **DisplayName** окна «**Свойства»**.  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle> можно указать в поле **Корреляция** в окне **Свойства** в области конструктора операций **InitializeCorrelation**.  
  
 Щелчок кнопки с многоточием рядом с полем **CorrelationData** в окне **Свойства** или рядом с указанием «Вид…» в области конструктора операций **InitializeCorrelation** отображает диалоговое окно **Инициализация корреляции**, в котором можно указать дескриптор взаимосвязи и пары ключ\-значение, которые используются при его инициализации.[!INCLUDE[crabout](../test/includes/crabout_md.md)] об использовании этого диалогового окна см. в разделе [Диалоговое окно редактора коллекций типов](../workflow-designer/type-collection-editor-dialog-box.md).  
  
### Свойства InitializeCorrelation  
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.InitializeCorrelation> и описано их использование в конструкторе.Эти свойства можно изменить в окне «**Свойства**» или в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>.По умолчанию используется InitializeCorrelation.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Нет|<xref:System.ServiceModel.Activities.CorrelationHandle> используется для привязки действий рабочих процессов в корреляции.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Нет|Словарь данных корреляции привязывает сообщения к данному экземпляру рабочего потока.<br /><br /> Диалоговое окно **Инициализация корреляции** можно использовать для настройки <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] использовании этого диалогового окна см. раздел [Диалоговое окно редактора коллекций типов](../workflow-designer/type-collection-editor-dialog-box.md).|  
  
## См. также  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)