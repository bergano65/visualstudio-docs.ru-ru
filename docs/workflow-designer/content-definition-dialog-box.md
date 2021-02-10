---
title: Диалоговое окно «Определение содержимого конструктор рабочих процессов»
description: Узнайте, как можно использовать диалоговое окно Определение содержимого для настройки свойств содержимого действий Send, Receive, SendReply и ReceiveReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a25d049b17381c49bfa1b4a5544972b6dc5fe499
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955649"
---
# <a name="content-definition-dialog-box"></a>Диалоговое окно «Определение содержимого»

Диалоговое окно " **Определение содержимого** " используется в конструктор рабочих процессов для настройки свойств **содержимого** <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> действий,, <xref:System.ServiceModel.Activities.SendReply> и <xref:System.ServiceModel.Activities.ReceiveReply> . Дополнительные сведения о конструкторах действий, использующих это поле, см. в статьях [Отправка](../workflow-designer/send-activity-designer.md), [Получение](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)и [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна « **Инициализация корреляции** ».

|Элемент пользовательского интерфейса|Описание|
|-|-----------------|
|**Сообщение**|Задает содержимое сообщения с текстовым полем «выражение **данных сообщения** » и типом с помощью раскрывающегося списка **тип сообщения** . По умолчанию в **определении содержимого** используется объект <xref:System.ServiceModel.Activities.ReceiveMessageContent> , который принимает <xref:System.ServiceModel.Channels.Message> тип контракта сообщения или в определении службы рабочего процесса.|
|**Параметры**|Выберите переключатель **Параметры** , который будет использоваться <xref:System.ServiceModel.Activities.ReceiveParametersContent> , если требуется контракт данных. Используйте сетку данных для задания универсальной коллекции пар «ключ/значение» <xref:System.Activities.OutArgument>, чьи значения присваиваются параметрам переменных в текущем рабочем процессе.|

Диалоговое окно " **Определение содержимого** " используется конструкторами **отправки**, **получения**, **ReceiveAndSendReply** и **SendAndReceiveReply** . Доступ к ним в каждом варианте одинаков, и для иллюстрации процедуры используется вариант Receive.

Конструктор операций **получения** можно перетащить из **панели элементов** в конструктор рабочих процессов область, где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите конструктор действий **получения** и нажмите кнопку с многоточием рядом с текстом (содержимое) для свойства **содержимое** в сетке свойств, чтобы отобразить диалоговое окно **Определение содержимого** .

Содержимое может быть указано в разделе **сообщения** для <xref:System.ServiceModel.Activities.ReceiveMessageContent> действия или в разделе **параметров** для <xref:System.ServiceModel.Activities.ReceiveParametersContent> действия.

## <a name="see-also"></a>См. также раздел

- [Справка по пользовательскому интерфейсу конструктора рабочих процессов](browse-and-select-a-dotnet-type-dialog-box.md)