---
title: Конструктор рабочих процессов - конструктор шаблона ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f6f3f874d00dff8a171a169dca6fe2d94f14fe6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648761"
---
# <a name="receiveandsendreply-template-designer"></a>Конструктор шаблона ReceiveAndSendReply

**ReceiveAndSendReply** шаблон используется для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> действий. Действия являются частью <xref:System.Activities.Statements.Sequence> действие того они соотносятся как часть шаблона обмена сообщениями запрос ответ на сервере.

## <a name="the-receiveandsendreply-template"></a>Шаблон ReceiveAndSendReply

Добавление **ReceiveAndSendReply** шаблон выполнит все три операции Помимо создания <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> действий с <xref:System.Activities.Statements.Sequence> действия:

- Настраивает <xref:System.ServiceModel.Activities.Receive.OperationName%2A> и <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> свойства <xref:System.ServiceModel.Activities.Receive> действия.

- Привязывает свойство <xref:System.ServiceModel.Activities.SendReply.Request%2A> действия <xref:System.ServiceModel.Activities.Receive> к действию <xref:System.ServiceModel.Activities.Send>.

- Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="use-the-receiveandsendreply-template-designer"></a>Используйте конструктор шаблона ReceiveAndSendReply

Доступ **ReceiveAndSendReply** конструктора действий в **Messaging** категории **элементов**. **ReceiveAndSendReply** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия. Удаление конструктора действий создает <xref:System.ServiceModel.Activities.Receive> действие, которое можно настроить с помощью **отправки** конструктора действий и связанным <xref:System.ServiceModel.Activities.SendReply> , можно настроить с помощь конструктора SendReplyToReceive.

Дополнительные сведения об использовании **Receive** конструктор для настройки <xref:System.ServiceModel.Activities.Receive> действия, см. в разделе [получать конструктора действий](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Свойства SendReply

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.SendReply> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые ― в области конструктора рабочих процессов.

| Имя свойства | Обязательно | Использование |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Необязательное понятное имя действия <xref:System.ServiceModel.Activities.SendReply>. По умолчанию используется SendReplyToReceive.<br /><br /> Несмотря на то что использование нестандартное значение для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, рекомендуется использовать такое значение. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Ссылка на действие <xref:System.ServiceModel.Activities.Receive>, связанное с этим действием <xref:System.ServiceModel.Activities.SendReply>. Это свойство не должно быть **null**. Действия <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> используются на сервере вместе для моделирования обмена сообщениями по шаблону «запрос–ответ». Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. В конструкторе, это свойство нельзя изменить, так как оно автоматически привязывается к <xref:System.ServiceModel.Activities.Send> действия, из которого был создан <xref:System.ServiceModel.Activities.SendReply> действия. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Измените это свойство, нажав кнопку с многоточием рядом с полем **содержимого** поле в таблице свойств или нажав **определить** рядом с пунктом **содержимого** метка на  **Получать** рабочей области конструктора действий. Как отобразить **определение содержимого** диалоговое окно. Дополнительные сведения о том, как использовать это окно, см. в разделе [содержимого диалогового окна определения](../workflow-designer/content-definition-dialog-box.md) раздела. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом с полем <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> свойства в сетке свойств, чтобы открыть **Добавление инициализаторов корреляции** диалоговое окно. Дополнительные сведения об использовании это окно, см. в разделе [CorrelationInitializers диалоговое окно Добавление](../workflow-designer/add-correlationinitializers-dialog-box.md) раздела. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Указывает заголовок действия сообщения. Если явно не задано его значение по умолчанию:<br /><br /> <strong>https://tempuri.org/{service контракта пространство имен} / {имя контракта службы} / {имя операции}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Указывает, нужно ли сохранять экземпляр рабочего процесса до отправки ответного сообщения. Значение по умолчанию — **false**. |

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)