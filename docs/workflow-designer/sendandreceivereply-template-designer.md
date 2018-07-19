---
title: Конструктор рабочих процессов - конструктор шаблона SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 282ba94c026b885cb6f8250b33beb98616376e8d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755815"
---
# <a name="sendandreceivereply-template-designer"></a>Конструктор шаблона SendAndReceiveReply

**SendAndReceiveReply** шаблон используется для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> действий. Действия являются частью <xref:System.Activities.Statements.Sequence> действие того они соотносятся как часть шаблона обмена сообщениями запрос ответ на стороне клиента.

## <a name="the-sendandreceivereply-template"></a>Шаблон SendAndReceiveReply

Добавление **SendAndReceiveReply** шаблон выполнит все три операции Помимо создания <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> действий в <xref:System.Activities.Statements.Sequence> действия:

- Настраивает <xref:System.ServiceModel.Activities.Send.OperationName%2A> и <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> свойства <xref:System.ServiceModel.Activities.Send> действия.

- Привязывает свойство <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> действия <xref:System.ServiceModel.Activities.ReceiveReply> к действию <xref:System.ServiceModel.Activities.Send>.

- Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="use-the-sendandreceivereply-template-designer"></a>Используйте конструктор шаблона SendAndReceiveReply

Доступ **SendAndReceiveReply** конструктора действий в **Messaging** категории **элементов**. **SendAndReceiveReply** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия. Удаление конструктора действий создает <xref:System.ServiceModel.Activities.Send> действие, которое можно настроить с помощью **отправки** конструктора действий и связанным <xref:System.ServiceModel.Activities.ReceiveReply> , можно настроить с помощью **ReceiveReplyForSend** конструктора.

Дополнительные сведения об использовании **отправки** конструктор для настройки <xref:System.ServiceModel.Activities.Send> действия, см. в разделе [отправки](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Свойства ReceiveReply

В следующей таблице показаны <xref:System.ServiceModel.Activities.ReceiveReply> свойства и показывается, как они используются в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые ― в области конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.ReceiveReply>. По умолчанию - ReceiveReplyForSend.<br /><br /> Несмотря на то что использование нестандартное значение для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, рекомендуется использовать такое значение.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|Да|Ссылка на действие <xref:System.ServiceModel.Activities.Send>, связанное с этим действием <xref:System.ServiceModel.Activities.ReceiveReply>. Это свойство не должно быть **null**. Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> используются совместно на клиенте для моделирования обмена сообщениями по принципу «запрос–ответ». Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. В конструкторе, это свойство нельзя изменить, так как оно автоматически привязывается к <xref:System.ServiceModel.Activities.Send> действия, из которого был создан <xref:System.ServiceModel.Activities.ReceiveReply> действия.|
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Измените это свойство, нажав кнопку с многоточием рядом с полем **содержимого** поле, в сетке свойств или нажав **определить** рядом с пунктом **содержимого** метки на **Receive** рабочей области конструктора действий. Как отобразить **определение содержимого** диалоговое окно. Дополнительные сведения о том, как использовать это окно, см. в разделе [содержимого диалогового окна определения](../workflow-designer/content-definition-dialog-box.md).|
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом с полем <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> свойства в сетке свойств, чтобы открыть **Добавление инициализаторов корреляции** диалоговое окно. Дополнительные сведения об использовании это окно, см. в разделе [CorrelationInitializers диалоговое окно Добавление](../workflow-designer/add-correlationinitializers-dialog-box.md).|
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|Указывает заголовок действия сообщения. Если явно не задано его значение по умолчанию:<br /><br /> **https://tempuri.org/{service контракта пространство имен} / {имя контракта службы} / {имя операции}.**|

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)