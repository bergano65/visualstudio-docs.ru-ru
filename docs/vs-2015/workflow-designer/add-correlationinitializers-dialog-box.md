---
title: Диалоговое окно "Добавление CorrelationInitializers" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1402b90dfc78068546b510ce6b85379b1695f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672041"
---
# <a name="add-correlationinitializers-dialog-box"></a>Диалоговое окно «Добавление инициализаторов корреляции»
Диалоговое окно **Добавление инициализаторов корреляции** используется в [!INCLUDE[wfd1](../includes/wfd1-md.md)] для настройки свойств **CorrelationInitializers** <xref:System.ServiceModel.Activities.Send> действий,, <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> и <xref:System.ServiceModel.Activities.ReceiveReply> . [!INCLUDE[crabout](../includes/crabout-md.md)] Конструкторы действий, использующие это поле, см. в разделах [Отправка](../workflow-designer/send-activity-designer.md), [Получение](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)и [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 Инициализаторы корреляции в коллекции, указанной данным диалоговым окном, могут инициализировать корреляции на основе запроса, контекстной, обратного вызова или корреляции «запрос-ответ» между действиями обмена сообщениями.

 В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна **Добавление инициализаторов корреляции** .

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Добавить инициализатор**|Щелкните поле **Добавить инициализацию** , чтобы добавить дополнительный инициализатор в коллекцию.|
|**Тип корреляции**|Указывает тип инициализатора корреляции. Может быть выбран один из четырех типов.<br /><br /> 1. инициализатор корреляции обратных вызовов для указания <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. инициализатор корреляции контекста для указания <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. инициализатор корреляции "запрос-ответ" для указания <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. инициализатор корреляции запроса для указания <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> Изменение **коррелатионтипе**<br /><br /> 1. Tab для конкретной строки в сетке **добавления инициализатора** .<br />2. Нажмите клавиши CTRL + TAB, чтобы установить фокус на **коррелатионтипекомбобокс**<br />3. Нажмите клавиши Alt + стрелка вниз, чтобы открыть окно **ComboBox** и изменить его.|
|**Запросы XPath**|Пара «ключ-значение», содержащая запросы для извлечения данных корреляции из входящих и исходящих сообщений. Данный список действителен только при использовании типов <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Вызов диалогового окна «Добавление инициализаторов корреляции»
 Диалоговое окно **Добавление инициализаторов корреляции** используется конструкторами **отправки**, **получения**, **ReceiveAndSendReply**и **SendAndReceiveReply** . Доступ к ним аналогичен в каждом случае, и в этом случае для демонстрации процедуры используется конструктор **Receive** .

 Конструктор операций **получения** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите конструктор действий **получения** и нажмите кнопку с многоточием рядом с текстом (коллекция) для свойства **CorrelationInitializers** в сетке свойств в диалоговом окне **Добавление инициализаторов корреляции** .

## <a name="see-also"></a>См. также:
 [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)