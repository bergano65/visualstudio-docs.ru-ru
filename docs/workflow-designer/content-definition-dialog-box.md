---
title: Конструктор рабочих процессов - диалоговое окно «Определение содержимого»
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f20a17cf7e01eafc75263bd2753d686908574752
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971671"
---
# <a name="content-definition-dialog-box"></a>Диалоговое окно «Определение содержимого»

**Определение содержимого** диалоговое окно используется в конструкторе рабочих процессов Windows для настройки **содержимого** свойства <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, и <xref:System.ServiceModel.Activities.ReceiveReply> действия. Дополнительные сведения о конструкторы действий, установите этот флажок, см. в разделе [отправки](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), и [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) разделы.

В следующей таблице описаны элементы пользовательского интерфейса (UI) **инициализация корреляции** диалоговое окно:

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Сообщение**|Задает содержимое с сообщения **сообщений данных** текстового поля выражения и тип с помощью **тип сообщений** раскрывающегося списка. По умолчанию **определение содержимого** использует <xref:System.ServiceModel.Activities.ReceiveMessageContent>, который ожидает <xref:System.ServiceModel.Channels.Message> или тип контракта сообщения в определении службы рабочих процессов.|
|**Параметры**|Нажмите кнопку **параметры** переключатель, чтобы использовать <xref:System.ServiceModel.Activities.ReceiveParametersContent>, который ожидает контракт данных. Используйте сетку данных для задания универсальной коллекции пар «ключ/значение» <xref:System.Activities.OutArgument>, чьи значения присваиваются параметрам переменных в текущем рабочем процессе.|

**Определение содержимого** используется диалоговое окно **отправки**, **Receive**, **ReceiveAndSendReply**, и  **SendAndReceiveReply** конструкторы. Доступ к ним в каждом варианте одинаков, и для иллюстрации процедуры используется вариант Receive.

**Receive** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите **Receive** конструктора действий и нажмите кнопку с многоточием рядом с текстом (содержимое) для **содержимого** свойства в сетке свойств для **определение содержимого**диалоговое окно.

Содержимое можно указать с помощью **сообщение** , в разделе <xref:System.ServiceModel.Activities.ReceiveMessageContent> действия или в **параметр** , в разделе <xref:System.ServiceModel.Activities.ReceiveParametersContent> действия.

## <a name="see-also"></a>См. также

- [Справка по пользовательскому интерфейсу конструктора рабочих процессов](../workflow-designer/workflow-designer-ui-help.md)