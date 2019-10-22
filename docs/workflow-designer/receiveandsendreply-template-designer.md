---
title: Конструктор шаблонов конструктор рабочих процессов-ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a816013f4eceb390a16e76a06814043aa0adaeb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650025"
---
# <a name="receiveandsendreply-template-designer"></a>Конструктор шаблона ReceiveAndSendReply

Шаблон **ReceiveAndSendReply** используется для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply>ных действий. Действия являются частью <xref:System.Activities.Statements.Sequence> действия и взаимосвязаны как часть шаблона обмена сообщениями типа "запрос-ответ" на сервере.

## <a name="the-receiveandsendreply-template"></a>Шаблон ReceiveAndSendReply

Добавление шаблона **ReceiveAndSendReply** делает три вещи, помимо создания <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> действий с помощью <xref:System.Activities.Statements.Sequence> действия:

- Настраивает свойства <xref:System.ServiceModel.Activities.Receive.OperationName%2A> и <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Receive>.

- Привязывает свойство <xref:System.ServiceModel.Activities.SendReply.Request%2A> действия <xref:System.ServiceModel.Activities.Receive> к действию <xref:System.ServiceModel.Activities.Send>.

- Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="use-the-receiveandsendreply-template-designer"></a>Использование конструктора шаблонов ReceiveAndSendReply

Доступ к конструктору действий **ReceiveAndSendReply** в категории **обмена сообщениями** **панели элементов**. Конструктор действий **ReceiveAndSendReply** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где обычно размещаются действия. При удалении конструктора действий создается <xref:System.ServiceModel.Activities.Receive> действие, которое можно настроить с помощью конструктора действий **отправки** , и коррелированные <xref:System.ServiceModel.Activities.SendReply>, которые можно настроить с помощью конструктора SendReplyToReceive.

Дополнительные сведения об использовании конструктора **получения** для настройки действия <xref:System.ServiceModel.Activities.Receive> см. в разделе [Конструктор операций получения](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Свойства SendReply

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.SendReply> и описано их использование в конструкторе. Эти свойства можно изменить в сетке свойства, а некоторые можно изменить на поверхности конструктор рабочих процессов.

| Имя свойства | Обязательное значение | Использование |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Необязательное понятное имя действия <xref:System.ServiceModel.Activities.SendReply>. По умолчанию используется SendReplyToReceive.<br /><br /> Хотя использование значения не по умолчанию для понятного <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, лучше использовать такое значение. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Ссылка на действие <xref:System.ServiceModel.Activities.Receive>, связанное с этим действием <xref:System.ServiceModel.Activities.SendReply>. Это свойство не может иметь **значение NULL**. Действия <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> используются на сервере вместе для моделирования обмена сообщениями по шаблону «запрос–ответ». Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. В конструкторе нельзя изменить это свойство, так как оно автоматически привязано к <xref:System.ServiceModel.Activities.Send> действию, из которого было создано действие <xref:System.ServiceModel.Activities.SendReply>. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Измените это свойство, нажав кнопку с многоточием рядом с полем **содержимое** в сетке свойств или нажав кнопку **определить** рядом с меткой **содержимое** в области конструктора действий **получения** . В обоих окнах отображается диалоговое окно **определения содержимого** . Дополнительные сведения об использовании этого поля см. в разделе [диалогового окна «Определение содержимого](../workflow-designer/content-definition-dialog-box.md) ». |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом со свойством <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> в сетке свойств, чтобы открыть диалоговое окно **Добавление инициализаторов корреляции** . Дополнительные сведения об использовании этого поля см. в разделе « [Добавление CorrelationInitializers в диалоговом окне](../workflow-designer/add-correlationinitializers-dialog-box.md) ». |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Указывает заголовок действия сообщения. Если параметр не задан явно, его значение по умолчанию равно:<br /><br /> <strong>https://tempuri.org/{service ое пространство имен контракта}/{сервице имя контракта} имя/{Оператион}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Указывает, нужно ли сохранять экземпляр рабочего процесса до отправки ответного сообщения. Значение по умолчанию — **false**. |

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)