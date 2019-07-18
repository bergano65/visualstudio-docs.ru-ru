---
title: Добавление диалогового окна CorrelationInitializers | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c90a2d0e0297a00454e38f428093a2f2db1e46d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977476"
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
 [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)