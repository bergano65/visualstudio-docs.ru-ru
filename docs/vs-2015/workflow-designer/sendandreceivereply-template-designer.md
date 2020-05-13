---
title: SendAndReceiveReply шаблон дизайнер (ru) Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395349"
---
# <a name="sendandreceivereply-template-designer"></a>Конструктор шаблона SendAndReceiveReply
Шаблон **SendAndReceiveReply** используется для создания пары предварительно <xref:System.ServiceModel.Activities.Send> настроенных <xref:System.ServiceModel.Activities.ReceiveReply> и <xref:System.Activities.Statements.Sequence> действий в рамках действия, которые коррелируются как часть шаблона обмена сообщениями запроса/ответа на клиенте.

## <a name="the-sendandreceivereply-template"></a>Шаблон SendAndReceiveReply
 Добавление шаблона **SendAndReceiveReply** делает <xref:System.ServiceModel.Activities.Send> три <xref:System.ServiceModel.Activities.ReceiveReply> вещи, <xref:System.Activities.Statements.Sequence> кроме создания и действий в рамках деятельности:

1. Настраивает свойства <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Send>.

2. Привязывает свойство <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> действия <xref:System.ServiceModel.Activities.ReceiveReply> к действию <xref:System.ServiceModel.Activities.Send>.

3. Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="using-the-sendandreceivereply-template-designer"></a>Использование конструктора шаблонов SendAndReceiveReply
 Дизайнер активности **SendAndReceiveReply** можно найти в категории **«Сообщения»** **в наборе инструментов,** [!INCLUDE[wfd2](../includes/wfd2-md.md)] доступ к которой можно найти, нажав на вкладку **Toolbox** (альтернативно, выберите **панель инструментов** из меню **View** или CTRL-ALT-X.)

 Конструктор активности **SendAndReceiveReply** может быть вытащен из [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Toolbox** и высажен на поверхность везде, где обычно размещаются действия. Это создает <xref:System.ServiceModel.Activities.Send> действие, которое может быть настроено с <xref:System.ServiceModel.Activities.ReceiveReply> конструктором активности **Отправить** и коррелирует, которое может быть настроено с конструктором **ReceiveReplyForSend.**

 [!INCLUDE[crabout](../includes/crabout-md.md)]с **Send** помощью конструктора <xref:System.ServiceModel.Activities.Send> Отправить для настройки действия, см. [Send](../workflow-designer/send-activity-designer.md)

 [!INCLUDE[crabout](../includes/crabout-md.md)]с помощью конструктора **ReceiveReplyForSend** для настройки <xref:System.ServiceModel.Activities.ReceiveReply> действия см.

### <a name="properties-of-receivereply"></a>Свойства ReceiveReply
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.ReceiveReply> и описано их использование в конструкторе. These properties can be edited in properties grid and some can be edited on [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer surface.

|                                 Имя свойства                                 | Обязательно |                                                                                                                                                                                                                                                                                                                                                        Использование                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Необязательное понятное имя действия <xref:System.ServiceModel.Activities.ReceiveReply>. По умолчанию - ReceiveReplyForSend.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Ссылка на действие <xref:System.ServiceModel.Activities.Send>, связанное с этим действием <xref:System.ServiceModel.Activities.ReceiveReply>. Это свойство не должно быть **недействительным.** <xref:System.ServiceModel.Activities.Send>и <xref:System.ServiceModel.Activities.ReceiveReply> действия используются вместе на клиенте для моделирования шаблона обмена сообщениями запроса/ответа. Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. Это свойство нельзя изменить в конструкторе, поскольку оно автоматически привязывается к действию <xref:System.ServiceModel.Activities.Send>, из которого было создано действие <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Изналивать это свойство, нажав кнопку эллипса рядом с полем **содержимого** в сетке свойств или нажав **на Define...** кнопка рядом с меткой **Содержимого** на поверхности дизайнера активности **Receive.** Оба отображения диалог **определения содержимого.** [!INCLUDE[crabout](../includes/crabout-md.md)]как использовать это поле, [Content Definition Dialog Box](../workflow-designer/content-definition-dialog-box.md) см.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку ellipsis <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> рядом с свойством в сетке свойств, чтобы открыть диалоговую коробку **Add Correlation Initialis.** [!INCLUDE[crabout](../includes/crabout-md.md)]с помощью этого окна, [см.](../workflow-designer/add-correlationinitializers-dialog-box.md)               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Указывает заголовок действия сообщения. Если значение не задано явным образом, устанавливается значение по умолчанию:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>См. также
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Инициализизировать корреляцию](../workflow-designer/initializecorrelation-activity-designer.md) [Получить](../workflow-designer/receive-activity-designer.md) [ReceiveandSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Отправить](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)