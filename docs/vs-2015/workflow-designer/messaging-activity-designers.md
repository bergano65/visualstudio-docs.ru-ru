---
title: Конструкторы действий обмена сообщениями | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6fb06bea4cebf2558990d23f7ece5b4f8db5b95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658933"
---
# <a name="messaging-activity-designers"></a>Конструкторы действий обмена сообщениями
Конструкторы операций обмена сообщениями используются для создания и настройки действий обмена сообщениями, которые отправляют и получают сообщения [!INCLUDE[indigo1](../includes/indigo1-md.md)] из приложения [!INCLUDE[wf](../includes/wf-md.md)]. [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] представляет пять действий обмена сообщениями, а [!INCLUDE[wfd1](../includes/wfd1-md.md)] предоставляет два новых конструктора шаблонов, позволяющих управлять обменом сообщениями в пределах рабочего процесса. В подразделах этого раздела и перечисленных в следующей таблице приводится описание использования действия [!INCLUDE[wfd2](../includes/wfd2-md.md)] и конструкторов шаблонов.

## <a name="in-this-section"></a>Содержание

|Действие Message|Описание|
|----------------------|-----------------|
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.CorrelationScope>, обеспечивающее неявное управление дочерними действиями обмена сообщениями с объектом <xref:System.ServiceModel.Activities.CorrelationHandle>.|
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.InitializeCorrelation>, используемое для инициализации корреляции без отправки или получения сообщения.|
|[Receive](../workflow-designer/receive-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.Receive>, получающее сообщение от службы.|
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Создает предварительно настроенную пару действий <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> внутри действия <xref:System.Activities.Statements.Sequence>.|
|[Send](../workflow-designer/send-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.Send>, отправляющее сообщение службе.|
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Создает предварительно настроенную пару действий <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> внутри действия <xref:System.Activities.Statements.Sequence>.|
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Создает и настраивает действие <xref:System.ServiceModel.Activities.TransactedReceiveScope>, включающее поток транзакций в рабочий процесс.|

## <a name="reference"></a>Справочник
 <xref:System.Activities.Activity>

 <xref:System.ServiceModel.Activities.CorrelationScope>

 <xref:System.ServiceModel.Activities.Receive>

 <xref:System.ServiceModel.Activities.Send>

 <xref:System.ServiceModel.Activities.ReceiveReply>

 <xref:System.ServiceModel.Activities.SendReply>

 <xref:System.ServiceModel.Activities.TransactedReceiveScope>

## <a name="related-sections"></a>Связанные разделы
 Сведения о других типах конструкторов действий см. в следующих подразделах.

 [Поток управления](../workflow-designer/control-flow-activity-designers.md)

 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)

 [Блок-схема](../workflow-designer/flowchart-activity-designers.md)

 [Среда выполнения](../workflow-designer/runtime-activity-designers.md)

 [Примитивы](../workflow-designer/primitives-activity-designers.md)

 [Транзакция](../workflow-designer/transaction-activity-designers.md)

 [Коллекция](../workflow-designer/collection-activity-designers.md)

 [Обработка ошибок](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>Внешние ресурсы
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)