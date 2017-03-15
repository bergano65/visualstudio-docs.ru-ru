---
title: "Конструкторы действий обмена сообщениями | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Конструкторы действий обмена сообщениями
Конструкторы операций обмена сообщениями используются для создания и настройки действий обмена сообщениями, которые отправляют и получают сообщения [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] из приложения [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)].[!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] представляет пять действий обмена сообщениями, а [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] предоставляет два новых конструктора шаблонов, позволяющих управлять обменом сообщениями в пределах рабочего процесса.В подразделах этого раздела и перечисленных в следующей таблице приводится описание использования действия [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] и конструкторов шаблонов.  
  
## В этом подразделе  
  
|Действие Message|Описание|  
|----------------------|--------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.CorrelationScope>, обеспечивающее неявное управление дочерними действиями обмена сообщениями с объектом <xref:System.ServiceModel.Activities.CorrelationHandle>.|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.InitializeCorrelation>, используемое для инициализации корреляции без отправки или получения сообщения.|  
|[Receive](../workflow-designer/receive-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.Receive>, получающее сообщение от службы.|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Создает предварительно настроенную пару действий <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> внутри действия <xref:System.Activities.Statements.Sequence>.|  
|[Send](../workflow-designer/send-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.Send>, отправляющее сообщение службе.|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Создает предварительно настроенную пару действий <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> внутри действия <xref:System.Activities.Statements.Sequence>.|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.TransactedReceiveScope>, включающее поток транзакций в рабочий процесс.|  
  
## Ссылка  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## Связанные подразделы  
 Сведения о других типах конструкторов действий см. в следующих подразделах.  
  
 [Управление потоком](../workflow-designer/control-flow-activity-designers.md)  
  
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)  
  
 [Блок\-схема](../workflow-designer/flowchart-activity-designers.md)  
  
 [Среда выполнения](../workflow-designer/runtime-activity-designers.md)  
  
 [Базовые функции](../workflow-designer/primitives-activity-designers.md)  
  
 [Транзакция](../workflow-designer/transaction-activity-designers.md)  
  
 [Коллекция](../workflow-designer/collection-activity-designers.md)  
  
 [Обработка ошибок](../workflow-designer/error-handling-activity-designers.md)  
  
## Внешние ресурсы  
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)