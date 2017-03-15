---
title: "Диалоговое окно &#171;Определение содержимого&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "MessageContent.UI"
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Диалоговое окно &#171;Определение содержимого&#187;
Диалоговое окно **Определение содержимого** используется в [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] для настройки свойств **Content** для действий <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>и <xref:System.ServiceModel.Activities.ReceiveReply>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] конструкторах операций, использующих это поле, см. в разделах [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) и [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md).  
  
 В следующей таблице приведено описание элементов пользовательского интерфейса диалогового окна **Инициализация корреляции**.  
  
|Элемент пользовательского интерфейса|Описание|  
|------------------------------------------|--------------|  
|**Сообщение**|Задает содержимое сообщения при помощи текстового поля выражения **Данные сообщения**, а тип с помощью раскрывающегося списка **Тип сообщения**.По умолчанию **Определение содержимого** использует действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, ожидающее <xref:System.ServiceModel.Channels.Message> или тип контракта сообщения в определении службы рабочих процессов.|  
|**Параметры**|Щелкните переключатель **Параметры** для использования действия <xref:System.ServiceModel.Activities.ReceiveParametersContent>, ожидающего контракт данных.Используйте сетку данных для задания универсальной коллекции пар «ключ\/значение» <xref:System.Activities.OutArgument>, чьи значения присваиваются параметрам переменных в текущем рабочем процессе.|  
  
 Диалоговое окно **Определение содержимого** используется конструкторами **Send**, **Receive**, **ReceiveAndSendReply** и **SendAndReceiveReply**.Доступ к ним в каждом варианте одинаков, и для иллюстрации процедуры используется вариант Receive.  
  
 Конструктор действий **Receive** можно перетащить из **Области элементов** в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] в любое место, куда обычно помещаются действия.При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive.Выберите конструктор операций **Receive** и нажмите кнопку с многоточием рядом с текстом \(Содержимое\) для свойства **Содержимое** в таблице свойств для появления диалогового окна **Определение содержимого**.  
  
 Для действия <xref:System.ServiceModel.Activities.ReceiveMessageContent> содержимое можно указать внутри раздела **Сообщение**, а для действия <xref:System.ServiceModel.Activities.ReceiveParametersContent> — внутри раздела **Параметр**.  
  
## См. также  
 [Справка по пользовательскому интерфейсу конструктора рабочих процессов](../workflow-designer/workflow-designer-ui-help.md)