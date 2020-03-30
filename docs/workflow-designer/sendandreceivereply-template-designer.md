---
title: Дизайнер рабочего процесса - конструктор шаблонов SendAndReceiveReply
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
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395246"
---
# <a name="sendandreceivereply-template-designer"></a>Конструктор шаблона SendAndReceiveReply

Шаблон **SendAndReceiveReply** используется для создания пары предварительно <xref:System.ServiceModel.Activities.Send> настроенных и <xref:System.ServiceModel.Activities.ReceiveReply> действий. Действия являются частью <xref:System.Activities.Statements.Sequence> действия и коррелируются как часть шаблона обмена сообщениями запроса/ответа на клиента.

## <a name="the-sendandreceivereply-template"></a>Шаблон SendAndReceiveReply

Добавление шаблона **SendAndReceiveReply** делает три <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> вещи, <xref:System.Activities.Statements.Sequence> кроме создания и действий в рамках деятельности:

- Настраивает <xref:System.ServiceModel.Activities.Send.OperationName%2A> и <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> свойства <xref:System.ServiceModel.Activities.Send> деятельности.

- Привязывает свойство <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> действия <xref:System.ServiceModel.Activities.ReceiveReply> к действию <xref:System.ServiceModel.Activities.Send>.

- Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="use-the-sendandreceivereply-template-designer"></a>Используйте шаблон SendAndReceiveReply Designer

Доступ к разработчику активности **SendAndReceiveReply** в категории **«Сообщения»** **в наборе инструментов.** Конструктор активности **SendAndReceiveReply** может быть перевезен из **toolbox** и отброшен на поверхность конструктора рабочего процесса везде, где обычно размещаются действия. Удаление действия дизайнер <xref:System.ServiceModel.Activities.Send> создает деятельность, которая может быть настроена с <xref:System.ServiceModel.Activities.ReceiveReply> конструктором деятельности **Отправить** и коррелирует, которые могут быть настроены с **receiveReplyForSend** дизайнера.

Для получения дополнительной информации об использовании конструктора **Отправить** для настройки <xref:System.ServiceModel.Activities.Send> действия см. [Send](../workflow-designer/send-activity-designer.md)

### <a name="properties-of-receivereply"></a>Свойства ReceiveReply

В следующей <xref:System.ServiceModel.Activities.ReceiveReply> таблице показаны свойства и описано, как они используются в дизайнере. Эти свойства можно редактировать в сетке свойств, а некоторые можно редактировать на поверхности рабочего процесса Designer.

| Имя свойства | Обязательно | Использование |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Необязательное понятное имя действия <xref:System.ServiceModel.Activities.ReceiveReply>. По умолчанию - ReceiveReplyForSend.<br /><br /> Хотя использование значения без дефолта для <xref:System.Activities.Activity.DisplayName%2A> дружественных не является строго обязательным, лучше всего использовать такое значение. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Ссылка на действие <xref:System.ServiceModel.Activities.Send>, связанное с этим действием <xref:System.ServiceModel.Activities.ReceiveReply>. Это свойство не должно быть **недействительным.** <xref:System.ServiceModel.Activities.Send>и <xref:System.ServiceModel.Activities.ReceiveReply> действия используются вместе на клиенте для моделирования шаблона обмена сообщениями запроса/ответа. Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. В проекте вы не можете отредитрать это свойство, поскольку оно автоматически связано с <xref:System.ServiceModel.Activities.Send> действием, <xref:System.ServiceModel.Activities.ReceiveReply> из которого вы создали действие. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Отспособьте это свойство, нажав кнопку ellipsis рядом с полем **содержимого** в сетке свойств, или нажав кнопку **«Определение»** рядом с меткой **Content** на поверхности дизайнера активности **Receive.** Оба отображения диалог **определения содержимого.** Для получения дополнительной информации о том, как использовать это поле, [см.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку ellipsis <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> рядом с свойством в сетке свойств, чтобы открыть диалоговую коробку **Add Correlation Initialis.** Для получения дополнительной информации об использовании этого окна, [см.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Указывает заголовок действия сообщения. Если он явно не установлен, его значение по умолчанию:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Получить](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)