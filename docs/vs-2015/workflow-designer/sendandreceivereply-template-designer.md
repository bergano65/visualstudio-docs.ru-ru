---
title: Конструктор шаблонов SendAndReceiveReply | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395349"
---
# <a name="sendandreceivereply-template-designer"></a>Конструктор шаблона SendAndReceiveReply
Шаблон **SendAndReceiveReply** используется для создания пары предварительно настроенных и выполняемых <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> действий в рамках <xref:System.Activities.Statements.Sequence> действия, которое сопоставляется как часть шаблона обмена сообщениями типа "запрос-ответ" на клиенте.

## <a name="the-sendandreceivereply-template"></a>Шаблон SendAndReceiveReply
 Добавление шаблона **SendAndReceiveReply** делает три вещи, помимо создания <xref:System.ServiceModel.Activities.Send> действий и в <xref:System.ServiceModel.Activities.ReceiveReply> рамках <xref:System.Activities.Statements.Sequence> действия:

1. Настраивает свойства <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Send>.

2. Привязывает свойство <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> действия <xref:System.ServiceModel.Activities.ReceiveReply> к действию <xref:System.ServiceModel.Activities.Send>.

3. Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="using-the-sendandreceivereply-template-designer"></a>Использование конструктора шаблонов SendAndReceiveReply
 Конструктор действий **SendAndReceiveReply** можно найти в категории **Обмен сообщениями** **области элементов**, щелкнув вкладку **область элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать пункт **панель инструментов** в меню **вид** или CTRL + ALT + X).

 Конструктор действий **SendAndReceiveReply** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия. При этом создается <xref:System.ServiceModel.Activities.Send> действие, которое можно настроить с помощью конструктора действий **отправки** , и коррелированный <xref:System.ServiceModel.Activities.ReceiveReply> , который можно настроить с помощью конструктора **рецеивереплифорсенд** .

 [!INCLUDE[crabout](../includes/crabout-md.md)] сведения о настройке действия с помощью конструктора **отправки** <xref:System.ServiceModel.Activities.Send> см. в разделе [Send](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] сведения о настройке действия с помощью конструктора **рецеивереплифорсенд** <xref:System.ServiceModel.Activities.ReceiveReply> см. в следующем разделе.

### <a name="properties-of-receivereply"></a>Свойства ReceiveReply
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.ReceiveReply> и описано их использование в конструкторе. These properties can be edited in properties grid and some can be edited on [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer surface.

|                                 Имя свойства                                 | Обязательно |                                                                                                                                                                                                                                                                                                                                                        Использование                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  Неверно   |                                                                                                                                                                                            Необязательное понятное имя действия <xref:System.ServiceModel.Activities.ReceiveReply>. По умолчанию - ReceiveReplyForSend.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Верно   | Ссылка на действие <xref:System.ServiceModel.Activities.Send>, связанное с этим действием <xref:System.ServiceModel.Activities.ReceiveReply>. Это свойство не может иметь **значение NULL**. <xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply>действия и используются совместно на клиенте для моделирования шаблона обмена сообщениями "запрос-ответ". Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. Это свойство нельзя изменить в конструкторе, поскольку оно автоматически привязывается к действию <xref:System.ServiceModel.Activities.Send>, из которого было создано действие <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  Неверно   |                        Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Измените это свойство, нажав кнопку с многоточием рядом с полем **содержимое** в сетке свойств или нажав кнопку **определить...** рядом с меткой **содержимое** в области конструктора действий **получения** . В обоих окнах отображается диалоговое окно **определения содержимого** . [!INCLUDE[crabout](../includes/crabout-md.md)] об использовании этого поля см. в разделе [диалогового окна «Определение содержимого](../workflow-designer/content-definition-dialog-box.md) ».                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  Неверно   |              Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом со <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> свойством в сетке свойства, чтобы открыть диалоговое окно **Добавление инициализаторов корреляции** . [!INCLUDE[crabout](../includes/crabout-md.md)] с помощью этого поля см. раздел [Добавление CorrelationInitializers в диалоговом окне](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  Неверно   |                                                                                                                                                                                                                                               Указывает заголовок действия сообщения. Если значение не задано явным образом, устанавливается значение по умолчанию:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>См. также:
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Получение](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)