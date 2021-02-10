---
title: Конструктор шаблона SendAndReceiveReply
description: Узнайте, как можно использовать шаблон SendAndReceiveReply в конструктор рабочих процессов, чтобы создать пару предварительно настроенных действий Send и ReceiveReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02bcc4a812a541ea792a190dc21dfbeb3119c008
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943696"
---
# <a name="sendandreceivereply-template-designer"></a>Конструктор шаблона SendAndReceiveReply

Шаблон **SendAndReceiveReply** используется для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> действий и. Действия являются частью <xref:System.Activities.Statements.Sequence> действия и взаимосвязаны как часть шаблона обмена сообщениями типа "запрос-ответ" на клиенте.

## <a name="the-sendandreceivereply-template"></a>Шаблон SendAndReceiveReply

Добавление шаблона **SendAndReceiveReply** делает три вещи, помимо создания <xref:System.ServiceModel.Activities.Send> действий и <xref:System.ServiceModel.Activities.ReceiveReply> в рамках <xref:System.Activities.Statements.Sequence> действия:

- Настраивает <xref:System.ServiceModel.Activities.Send.OperationName%2A> Свойства и <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> для <xref:System.ServiceModel.Activities.Send> действия.

- Привязывает свойство <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> действия <xref:System.ServiceModel.Activities.ReceiveReply> к действию <xref:System.ServiceModel.Activities.Send>.

- Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="use-the-sendandreceivereply-template-designer"></a>Использование конструктора шаблонов SendAndReceiveReply

Доступ к конструктору действий **SendAndReceiveReply** в категории **обмена сообщениями** **панели элементов**. Конструктор действий **SendAndReceiveReply** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где обычно размещаются действия. При удалении конструктора действий создается <xref:System.ServiceModel.Activities.Send> действие, которое можно настроить с помощью конструктора действий **отправки** , и коррелированный <xref:System.ServiceModel.Activities.ReceiveReply> , который можно настроить с помощью конструктора **рецеивереплифорсенд** .

Дополнительные сведения об использовании конструктора **отправки** для настройки <xref:System.ServiceModel.Activities.Send> действия см. в разделе [Send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Свойства ReceiveReply

В следующей таблице показаны <xref:System.ServiceModel.Activities.ReceiveReply> Свойства и описано, как они используются в конструкторе. Эти свойства можно изменять в сетке свойств, а некоторые — в области конструктор рабочих процессов.

| Имя свойства | Обязательно | Использование |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Необязательное понятное имя действия <xref:System.ServiceModel.Activities.ReceiveReply>. По умолчанию - ReceiveReplyForSend.<br /><br /> Хотя использование нестандартного значения для понятного <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, лучше использовать такое значение. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Ссылка на действие <xref:System.ServiceModel.Activities.Send>, связанное с этим действием <xref:System.ServiceModel.Activities.ReceiveReply>. Это свойство не может иметь **значение NULL**. <xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply>действия и используются совместно на клиенте для моделирования шаблона обмена сообщениями "запрос-ответ". Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. В конструкторе нельзя изменить это свойство, так как оно автоматически привязано к <xref:System.ServiceModel.Activities.Send> действию, из которого было создано <xref:System.ServiceModel.Activities.ReceiveReply> действие. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Измените это свойство, нажав кнопку с многоточием рядом с полем **содержимое** в сетке свойств или нажав кнопку **определить** рядом с меткой **содержимое** в области конструктора действий **получения** . В обоих окнах отображается диалоговое окно **определения содержимого** . Дополнительные сведения об использовании этого поля см. в разделе [диалоговое окно "Определение содержимого"](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом со <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> свойством в сетке свойства, чтобы открыть диалоговое окно **Добавление инициализаторов корреляции** . Дополнительные сведения об использовании этого поля см. в разделе [Add CorrelationInitializers (Добавление диалогового окна](../workflow-designer/add-correlationinitializers-dialog-box.md)). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Указывает заголовок действия сообщения. Если параметр не задан явно, его значение по умолчанию равно:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>См. также раздел

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Получать](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)