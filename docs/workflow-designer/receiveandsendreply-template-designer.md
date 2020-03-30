---
title: Конструктор рабочего процесса - Конструктор шаблона ReceiveandSendReply
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
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395300"
---
# <a name="receiveandsendreply-template-designer"></a>Конструктор шаблона ReceiveAndSendReply

Шаблон **ReceiveAndSendReply** используется для создания пары предварительно <xref:System.ServiceModel.Activities.Receive> настроенных и <xref:System.ServiceModel.Activities.SendReply> действий. Действия являются частью <xref:System.Activities.Statements.Sequence> действия и коррелируются как часть шаблона обмена сообщениями запроса/ответа на сервере.

## <a name="the-receiveandsendreply-template"></a>Шаблон ReceiveAndSendReply

Добавление шаблона **ReceiveAndSendReply** делает три <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> вещи, <xref:System.Activities.Statements.Sequence> кроме создания и деятельности с деятельностью:

- Настраивает <xref:System.ServiceModel.Activities.Receive.OperationName%2A> и <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> свойства <xref:System.ServiceModel.Activities.Receive> деятельности.

- Привязывает свойство <xref:System.ServiceModel.Activities.SendReply.Request%2A> действия <xref:System.ServiceModel.Activities.Receive> к действию <xref:System.ServiceModel.Activities.Send>.

- Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="use-the-receiveandsendreply-template-designer"></a>Используйте шаблон-дизайнер ReceiveAndSendReply

Доступ к разработчику активности **ReceiveAndSendReply** в категории **«Сообщения»** **в наборе инструментов.** Конструктор деятельности **ReceiveAndSendReply** может быть перевезен из **панели инструментов** и сброшен на поверхность конструктора рабочего процесса, где бы обычно размещалось действия. Удаление действия дизайнер <xref:System.ServiceModel.Activities.Receive> создает деятельность, которая может быть настроена с <xref:System.ServiceModel.Activities.SendReply> конструктором деятельности **Отправить** и коррелирует, которые могут быть настроены с дизайнером SendReplyToReceive.

Для получения дополнительной информации об использовании дизайнера **Receive** для настройки <xref:System.ServiceModel.Activities.Receive> действия см. [Receive Activity Designer](../workflow-designer/receive-activity-designer.md)

### <a name="properties-of-sendreply"></a>Свойства SendReply

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.SendReply> и описано их использование в конструкторе. Эти свойства можно редактировать в сетке свойств, а некоторые можно редактировать на поверхности рабочего процесса Designer.

| Имя свойства | Обязательно | Использование |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Необязательное понятное имя действия <xref:System.ServiceModel.Activities.SendReply>. По умолчанию используется SendReplyToReceive.<br /><br /> Хотя использование значения без дефолта для <xref:System.Activities.Activity.DisplayName%2A> дружественных не является строго обязательным, лучше всего использовать такое значение. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Ссылка на действие <xref:System.ServiceModel.Activities.Receive>, связанное с этим действием <xref:System.ServiceModel.Activities.SendReply>. Это свойство не должно быть **недействительным.** <xref:System.ServiceModel.Activities.Receive>и <xref:System.ServiceModel.Activities.SendReply> действия используются вместе на сервере для моделирования шаблона обмена сообщениями запроса/ответа. Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. В проекте вы не можете отредитрать это свойство, поскольку оно автоматически связано с <xref:System.ServiceModel.Activities.Send> действием, <xref:System.ServiceModel.Activities.SendReply> из которого вы создали действие. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Отспособьте это свойство, нажав кнопку ellipsis рядом с полем **содержимого** в сетке свойств, или нажав кнопку **«Определение»** рядом с меткой **Содержимого** на поверхности дизайнера активности **Receive.** Оба отображения диалог **определения содержимого.** Для получения дополнительной информации о том, как использовать это поле, см. [Content Definition Dialog Box](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку ellipsis <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> рядом с свойством в сетке свойств, чтобы открыть диалоговую коробку **Add Correlation Initialis.** Для получения дополнительной информации об использовании этого окна, [см.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Указывает заголовок действия сообщения. Если он явно не установлен, его значение по умолчанию:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Указывает, нужно ли сохранять экземпляр рабочего процесса до отправки ответного сообщения. По умолчанию используется значение **false**. |

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Получить](../workflow-designer/receive-activity-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)