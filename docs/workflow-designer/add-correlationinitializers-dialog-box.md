---
title: CorrelationInitializers диалоговое окно добавления | Документы Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1dda343758925e1cece9d796bee8f0d225729c36
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="add-correlationinitializers-dialog-box"></a>Диалоговое окно «Добавление инициализаторов корреляции»
**Добавление инициализаторов корреляции** диалоговое окно используется в конструкторе рабочих процессов Windows для настройки **CorrelationInitializers** свойства <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, и <xref:System.ServiceModel.Activities.ReceiveReply> действий. Дополнительные сведения о конструкторы действий, установите этот флажок, см. в разделе [отправки](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), и [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) разделы.

 Инициализаторы корреляции в коллекции, указанной данным диалоговым окном, могут инициализировать корреляции на основе запроса, контекстной, обратного вызова или корреляции «запрос-ответ» между действиями обмена сообщениями.

 В следующей таблице описаны элементы пользовательского интерфейса (UI) **Добавление инициализаторов корреляции** диалоговое окно.

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Добавить инициализатор**|Нажмите кнопку **добавить initialize** служит для добавления в коллекцию дополнительный инициализатор.|
|**Тип корреляции**|Указывает тип инициализатора корреляции. Может быть выбран один из четырех типов.<br /><br /> 1.  Инициализатор корреляции обратного вызова для указания <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Инициализатор контекстной корреляции для указания <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Инициализатор корреляции «запрос-ответ» для указания <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Инициализатор корреляции запросов для указания <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Чтобы изменить **типа корреляции**<br /><br /> 1.  Вкладка в указанную строку в **добавить инициализатор** DataGrid.<br />2.  Нажмите клавиши Ctrl + Tab, чтобы сфокусировать **CorrelationTypeComboBox**<br />3.  Нажмите клавиши Alt + Стрелка вниз для раскрытия **ComboBox** и изменить его.|
|**Запросы XPath**|Пара «ключ-значение», содержащая запросы для извлечения данных корреляции из входящих и исходящих сообщений. Данный список действителен только при использовании типов <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Вызов диалогового окна «Добавление инициализаторов корреляции»
 **Добавление инициализаторов корреляции** используется диалоговое окно **отправки**, **Receive**, **ReceiveAndSendReply**, и  **SendAndReceiveReply** конструкторы. Доступ к ним аналогичен в каждом случае и случаем, который включает в себя **Receive** конструктор используется здесь для иллюстрации процедуры.

 **Receive** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите **Receive** конструктора действий и нажмите кнопку с многоточием рядом с текстом (коллекция) для **CorrelationInitializers** свойства в сетке свойств для **добавить Инициализаторы корреляции** диалоговое окно.

## <a name="see-also"></a>См. также

- [Добавить диалоговое окно «взаимосвязь»](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)