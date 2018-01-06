---
title: "Диалоговое окно Определение содержимого | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: "3"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: c87180f1f1c0b2c578977021b6a9511e629d10bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="content-definition-dialog-box"></a>Диалоговое окно «Определение содержимого»
**Определение содержимого** диалоговое окно используется в [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] Настройка **содержимого** свойства <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, и <xref:System.ServiceModel.Activities.ReceiveReply> действия. [!INCLUDE[crabout](../test/includes/crabout_md.md)]конструкторы действий, используйте это поле в разделе [отправки](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), и [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) разделы.  
  
 В следующей таблице описаны элементы пользовательского интерфейса (UI) **инициализация корреляции** диалоговое окно.  
  
|Элемент пользовательского интерфейса|Описание:|  
|----------------|-----------------|  
|**Сообщение**|Задает содержимое с сообщения **сообщений данных** текстового поля выражения и тип с помощью **тип сообщений** раскрывающегося списка. По умолчанию **определение содержимого** использует <xref:System.ServiceModel.Activities.ReceiveMessageContent>, который ожидает <xref:System.ServiceModel.Channels.Message> или тип контракта сообщения в определении службы рабочих процессов.|  
|**Параметры**|Нажмите кнопку **параметры** переключатель, чтобы использовать <xref:System.ServiceModel.Activities.ReceiveParametersContent>, который ожидает контракт данных. Используйте сетку данных для задания универсальной коллекции пар «ключ/значение» <xref:System.Activities.OutArgument>, чьи значения присваиваются параметрам переменных в текущем рабочем процессе.|  
  
 **Определение содержимого** используется диалоговое окно **отправки**, **Receive**, **ReceiveAndSendReply**, и  **SendAndReceiveReply** конструкторы. Доступ к ним в каждом варианте одинаков, и для иллюстрации процедуры используется вариант Receive.  
  
 **Receive** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите **Receive** конструктора действий и нажмите кнопку с многоточием рядом с текстом (содержимое) для **содержимого** свойства в сетке свойств для **определение содержимого**диалоговое окно.  
  
 Содержимое можно указать с помощью **сообщение** , в разделе <xref:System.ServiceModel.Activities.ReceiveMessageContent> действия или в **параметр** , в разделе <xref:System.ServiceModel.Activities.ReceiveParametersContent> действия.  
  
## <a name="see-also"></a>См. также  
 [Справка по пользовательскому интерфейсу конструктора рабочих процессов](../workflow-designer/workflow-designer-ui-help.md)