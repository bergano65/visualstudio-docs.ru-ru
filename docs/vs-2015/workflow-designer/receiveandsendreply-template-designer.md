---
title: ReceiveAndSendReply шаблон дизайнер (ru) Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395390"
---
# <a name="receiveandsendreply-template-designer"></a>Конструктор шаблона ReceiveAndSendReply
Шаблон **ReceiveAndSendReply** используется для создания пары предварительно <xref:System.ServiceModel.Activities.Receive> настроенных <xref:System.ServiceModel.Activities.SendReply> и <xref:System.Activities.Statements.Sequence> действий в рамках действия, которые коррелируются как часть шаблона обмена сообщениями запроса/ответа на сервере.

## <a name="the-receiveandsendreply-template"></a>Шаблон ReceiveAndSendReply
 Добавление шаблона **ReceiveAndSendReply** делает <xref:System.ServiceModel.Activities.Receive> три <xref:System.ServiceModel.Activities.SendReply> вещи, <xref:System.Activities.Statements.Sequence> кроме создания и деятельности с деятельностью:

1. Настраивает свойства <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Receive>.

2. Привязывает свойство <xref:System.ServiceModel.Activities.SendReply.Request%2A> действия <xref:System.ServiceModel.Activities.Receive> к действию <xref:System.ServiceModel.Activities.Send>.

3. Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="using-the-receiveandsendreply-template-designer"></a>Использование конструктора шаблонов ReceiveAndSendReply
 Дизайнер деятельности **ReceiveAndSendReply** можно найти в категории **«Сообщения»** **в наборе**инструментов, [!INCLUDE[wfd2](../includes/wfd2-md.md)] доступ к которой можно получить, нажав на вкладку **Toolbox** (Альтернативно выберите панель **инструментов** из меню **View** или CTRL-ALT-X.)

 Конструктор деятельности **ReceiveAndSendReply** может быть вытащен из [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Toolbox** и высажен на поверхность везде, где обычно размещаются действия. Это создает <xref:System.ServiceModel.Activities.Receive> действие, которое может быть настроено с <xref:System.ServiceModel.Activities.SendReply> конструктором активности **Отправить** и коррелирует, которое может быть настроено с конструктором SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)]с помощью дизайнера <xref:System.ServiceModel.Activities.Receive> **Receive** для [Receive](../workflow-designer/receive-activity-designer.md) настройки действия см.

 [!INCLUDE[crabout](../includes/crabout-md.md)]с помощью конструктора **SendReplyToReceive** для настройки <xref:System.ServiceModel.Activities.SendReply> действия см.

### <a name="properties-of-sendreply"></a>Свойства SendReply
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.SendReply> и описано их использование в конструкторе. These properties can be edited in properties grid and some can be edited on [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer surface.

|                               Имя свойства                                | Обязательно |                                                                                                                                                                                                                                                                                                                                                      Использование                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            Необязательное понятное имя действия <xref:System.ServiceModel.Activities.SendReply>. По умолчанию используется SendReplyToReceive.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Ссылка на действие <xref:System.ServiceModel.Activities.Receive>, связанное с этим действием <xref:System.ServiceModel.Activities.SendReply>. Это свойство не должно быть **недействительным.** <xref:System.ServiceModel.Activities.Receive>и <xref:System.ServiceModel.Activities.SendReply> действия используются вместе на сервере для моделирования шаблона обмена сообщениями запроса/ответа. Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. Это свойство нельзя изменить в конструкторе, поскольку оно автоматически привязывается к действию <xref:System.ServiceModel.Activities.Send>, из которого было создано действие <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Изналивать это свойство, нажав кнопку эллипса рядом с полем **содержимого** в сетке свойств или нажав **на Define...** кнопка рядом с меткой **Содержимого** на поверхности дизайнера активности **Receive.** Оба отображения диалог **определения содержимого.** [!INCLUDE[crabout](../includes/crabout-md.md)]как использовать это поле, [Content Definition Dialog Box](../workflow-designer/content-definition-dialog-box.md) см.                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку ellipsis <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> рядом с свойством в сетке свойств, чтобы открыть диалоговую коробку **Add Correlation Initialis.** [!INCLUDE[crabout](../includes/crabout-md.md)]с помощью этого окна, [см.](../workflow-designer/add-correlationinitializers-dialog-box.md)            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              Указывает заголовок действия сообщения. Если значение не задано явным образом, устанавливается значение по умолчанию:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          Указывает, нужно ли сохранять экземпляр рабочего процесса до отправки ответного сообщения. По умолчанию используется значение **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>См. также
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Инициализизировать корреляцию](../workflow-designer/initializecorrelation-activity-designer.md) [Получить](../workflow-designer/receive-activity-designer.md) [Отправить](../workflow-designer/send-activity-designer.md) [SendandReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)