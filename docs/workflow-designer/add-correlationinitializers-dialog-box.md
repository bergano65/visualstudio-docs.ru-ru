---
title: Диалоговое окно "Добавление CorrelationInitializers"
description: Узнайте, как можно использовать диалоговое окно Добавление инициализаторов корреляции в конструктор рабочих процессов для настройки свойств CorrelationInitializers действий Send, Receive и SendReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ca78cea409f559583507fd4b5b7c9fc43f9a5ffc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963735"
---
# <a name="add-correlationinitializers-dialog-box"></a>Диалоговое окно «Добавление инициализаторов корреляции»

Диалоговое окно **Добавление инициализаторов корреляции** используется в конструктор рабочих процессов для настройки свойств **CorrelationInitializers** <xref:System.ServiceModel.Activities.Send> действий,, <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> и <xref:System.ServiceModel.Activities.ReceiveReply> . Дополнительные сведения о конструкторах действий, использующих это поле, см. в статьях [Отправка](../workflow-designer/send-activity-designer.md), [Получение](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)и [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Инициализаторы корреляции в коллекции, указанной в этом диалоговом окне, могут инициализировать следующие корреляции между действиями обмена сообщениями:

- на основе запросов
- контекст
- контекст обратного вызова
- запрос-ответ

В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса в диалоговом окне **Добавление инициализаторов корреляции** .

|Элемент пользовательского интерфейса|Описание|
|-|-----------------|
|**Добавить инициализатор**|Щелкните поле **Добавить инициализацию** , чтобы добавить дополнительный инициализатор в коллекцию.|
|**Тип корреляции**|Указывает тип инициализатора корреляции. Может быть выбран один из четырех типов.<br /><br /> 1. инициализатор корреляции обратных вызовов для указания <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. инициализатор корреляции контекста для указания <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. инициализатор корреляции "запрос-ответ" для указания <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. инициализатор корреляции запроса для указания <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> Изменение **коррелатионтипе**<br /><br /> 1. Tab для конкретной строки в сетке **добавления инициализатора** .<br />2. чтобы установить фокус на **коррелатионтипекомбобокс**, нажмите клавиши **CTRL** + **Tab**.<br />3. Нажмите клавиши Alt + стрелка вниз, чтобы открыть окно **ComboBox** и изменить его.|
|**Запросы XPath**|Пара «ключ-значение», содержащая запросы для извлечения данных корреляции из входящих и исходящих сообщений. Данный список действителен только при использовании типов <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Вызов диалогового окна «Добавление инициализаторов корреляции»

 Диалоговое окно **Добавление инициализаторов корреляции** используется конструкторами **отправки**, **получения**, **ReceiveAndSendReply** и **SendAndReceiveReply** . Доступ к ним аналогичен в каждом случае, и в этом случае для демонстрации процедуры используется конструктор **Receive** .

 Конструктор операций **получения** можно перетащить из **панели элементов** в конструктор рабочих процессовную поверхность, где будут размещены действия. При удалении конструктора операции **получения** создается <xref:System.ServiceModel.Activities.Receive> действие со значением Receive, заданным по умолчанию <xref:System.Activities.Activity.DisplayName%2A> . Выберите конструктор действий **получения** и нажмите кнопку с многоточием рядом с текстом (коллекция) для свойства **CorrelationInitializers** в сетке свойств в диалоговом окне **Добавление инициализаторов корреляции** .

## <a name="see-also"></a>См. также раздел

- [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)
