---
title: Диалоговое окно Определение содержимого | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 17b5b5609718dce1347928be491e8817b5796e4d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992763"
---
# <a name="content-definition-dialog-box"></a>Диалоговое окно «Определение содержимого»
**Определение содержимого** диалоговое окно используется в [!INCLUDE[wfd1](../includes/wfd1-md.md)] Настройка **содержимого** свойства <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, и <xref:System.ServiceModel.Activities.ReceiveReply> действия. [!INCLUDE[crabout](../includes/crabout-md.md)] конструкторах операций, использующих это поле, см. в разделе [отправки](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), и [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) разделы.  
  
 В следующей таблице описаны элементы пользовательского интерфейса (UI) **инициализация корреляции** диалоговое окно.  
  
|Элемент пользовательского интерфейса|Описание|  
|----------------|-----------------|  
|**Сообщение**|Задает содержимое сообщения при помощи **сообщений данных** текстовом поле выражения и типа с помощью **тип сообщений** поле с раскрывающимся списком. По умолчанию **определение содержимого** использует <xref:System.ServiceModel.Activities.ReceiveMessageContent>, который ожидает <xref:System.ServiceModel.Channels.Message> или тип контракта сообщения в определении службы рабочих процессов.|  
|**Параметры**|Нажмите кнопку **параметры** переключатель, чтобы использовать <xref:System.ServiceModel.Activities.ReceiveParametersContent>, который ожидает контракт данных. Используйте сетку данных для задания универсальной коллекции пар «ключ/значение» <xref:System.Activities.OutArgument>, чьи значения присваиваются параметрам переменных в текущем рабочем процессе.|  
  
 **Определение содержимого** используется диалоговое окно **отправки**, **Receive**, **ReceiveAndSendReply**, и  **SendAndReceiveReply** конструкторы. Доступ к ним в каждом варианте одинаков, и для иллюстрации процедуры используется вариант Receive.  
  
 **Receive** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите **Receive** конструктора действий и нажмите кнопку с многоточием, расположенную рядом с текстом (содержимое) для **содержимого** свойства в сетке свойств для **определение содержимого**диалоговое окно.  
  
 Содержимое должно лежать в пределах **сообщение** раздел <xref:System.ServiceModel.Activities.ReceiveMessageContent> действия или в **параметр** раздел <xref:System.ServiceModel.Activities.ReceiveParametersContent> действия.  
  
## <a name="see-also"></a>См. также  
 [Справка по пользовательскому интерфейсу конструктора рабочих процессов](../workflow-designer/workflow-designer-ui-help.md)