---
title: Конструктор шаблонов конструктор рабочих процессов-SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7c552e8bb94ed9035f25bdd40b7944458e61a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649957"
---
# <a name="sendandreceivereply-template-designer"></a>Конструктор шаблона SendAndReceiveReply

Шаблон **SendAndReceiveReply** используется для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply>ных действий. Действия являются частью <xref:System.Activities.Statements.Sequence> действия и взаимосвязаны как часть шаблона обмена сообщениями типа "запрос-ответ" на клиенте.

## <a name="the-sendandreceivereply-template"></a>Шаблон SendAndReceiveReply

Добавление шаблона **SendAndReceiveReply** делает три вещи, помимо создания <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> действий в рамках <xref:System.Activities.Statements.Sequence> действия.

- Настраивает свойства <xref:System.ServiceModel.Activities.Send.OperationName%2A> и <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Send>.

- Привязывает свойство <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> действия <xref:System.ServiceModel.Activities.ReceiveReply> к действию <xref:System.ServiceModel.Activities.Send>.

- Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="use-the-sendandreceivereply-template-designer"></a>Использование конструктора шаблонов SendAndReceiveReply

Доступ к конструктору действий **SendAndReceiveReply** в категории **обмена сообщениями** **панели элементов**. Конструктор действий **SendAndReceiveReply** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где обычно размещаются действия. При удалении конструктора действий создается <xref:System.ServiceModel.Activities.Send> действие, которое можно настроить с помощью конструктора действий **отправки** , и коррелированные <xref:System.ServiceModel.Activities.ReceiveReply>, которые можно настроить с помощью конструктора **рецеивереплифорсенд** .

Дополнительные сведения об использовании конструктора **отправки** для настройки действия <xref:System.ServiceModel.Activities.Send> см. в разделе [Send](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Свойства ReceiveReply

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.ReceiveReply> и описано, как они используются в конструкторе. Эти свойства можно изменять в сетке свойств, а некоторые — в области конструктор рабочих процессов.

| Имя свойства | Обязательное значение | Использование |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Необязательное понятное имя действия <xref:System.ServiceModel.Activities.ReceiveReply>. По умолчанию - ReceiveReplyForSend.<br /><br /> Хотя использование значения не по умолчанию для понятного <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, лучше использовать такое значение. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Ссылка на действие <xref:System.ServiceModel.Activities.Send>, связанное с этим действием <xref:System.ServiceModel.Activities.ReceiveReply>. Это свойство не может иметь **значение NULL**. Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> используются совместно на клиенте для моделирования обмена сообщениями по принципу «запрос–ответ». Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. В конструкторе нельзя изменить это свойство, так как оно автоматически привязано к <xref:System.ServiceModel.Activities.Send> действию, из которого было создано действие <xref:System.ServiceModel.Activities.ReceiveReply>. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Измените это свойство, нажав кнопку с многоточием рядом с полем **содержимое** в сетке свойств или нажав кнопку **определить** рядом с меткой **содержимое** в области конструктора действий **получения** . В обоих окнах отображается диалоговое окно **определения содержимого** . Дополнительные сведения об использовании этого поля см. в разделе [диалоговое окно "Определение содержимого"](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом со свойством <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> в сетке свойств, чтобы открыть диалоговое окно **Добавление инициализаторов корреляции** . Дополнительные сведения об использовании этого поля см. в разделе [Add CorrelationInitializers (Добавление диалогового окна](../workflow-designer/add-correlationinitializers-dialog-box.md)). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Указывает заголовок действия сообщения. Если параметр не задан явно, его значение по умолчанию равно:<br /><br /> <strong>https://tempuri.org/{service пространство имен контракта}/{сервице имя контракта} имя/{Оператион}.</strong> |

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)