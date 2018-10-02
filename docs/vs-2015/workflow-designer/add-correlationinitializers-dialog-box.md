---
title: Добавление диалогового окна CorrelationInitializers | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8543ebd784af13251663155327c2bfb9097b4904
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568926"
---
# <a name="add-correlationinitializers-dialog-box"></a>Диалоговое окно «Добавление инициализаторов корреляции»
**Добавление инициализаторов корреляции** диалоговое окно используется в [!INCLUDE[wfd1](../includes/wfd1-md.md)] Настройка **CorrelationInitializers** свойства <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, и <xref:System.ServiceModel.Activities.ReceiveReply> действий. [!INCLUDE[crabout](../includes/crabout-md.md)] конструкторах операций, использующих это поле, см. в разделе [отправки](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), и [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) разделы.  
  
 Инициализаторы корреляции в коллекции, указанной данным диалоговым окном, могут инициализировать корреляции на основе запроса, контекстной, обратного вызова или корреляции «запрос-ответ» между действиями обмена сообщениями.  
  
 В следующей таблице описаны элементы пользовательского интерфейса (UI) **Добавление инициализаторов корреляции** диалоговое окно.  
  
|Элемент пользовательского интерфейса|Описание|  
|----------------|-----------------|  
|**Добавить инициализатор**|Нажмите кнопку **добавить initialize** служит для добавления в коллекцию дополнительный инициализатор.|  
|**Тип корреляции**|Указывает тип инициализатора корреляции. Может быть выбран один из четырех типов.<br /><br /> 1.  Инициализатор корреляции обратного вызова для указания <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Инициализатор контекстной корреляции для указания <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Инициализатор корреляции «запрос-ответ» для указания <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Инициализатор корреляции запросов для указания <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Чтобы изменить **типа корреляции**<br /><br /> 1.  Вкладки в указанную строку в **добавить инициализатор** DataGrid.<br />2.  Нажмите клавиши Ctrl + Tab, чтобы установить фокус на **CorrelationTypeComboBox**<br />3.  Нажмите клавиши Alt + Стрелка вниз всплывает **ComboBox** и изменить его.|  
|**Запросы XPath**|Пара «ключ-значение», содержащая запросы для извлечения данных корреляции из входящих и исходящих сообщений. Данный список действителен только при использовании типов <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Вызов диалогового окна «Добавление инициализаторов корреляции»  
 **Добавление инициализаторов корреляции** используется диалоговое окно **отправки**, **Receive**, **ReceiveAndSendReply**, и  **SendAndReceiveReply** конструкторы. В каждом случае и вариант, который включает в себя доступ к ним аналогично **Receive** конструктор используется здесь для иллюстрации процедуры.  
  
 **Receive** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите **Receive** конструктора действий и нажмите кнопку с многоточием, расположенную рядом с текстом (коллекция) для **CorrelationInitializers** свойства в сетке свойств для **добавить Инициализаторы корреляции** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Добавление диалогового окна корреляции](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)