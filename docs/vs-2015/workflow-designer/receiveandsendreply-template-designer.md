---
title: Конструктор шаблонов ReceiveAndSendReply | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395390"
---
# <a name="receiveandsendreply-template-designer"></a>Конструктор шаблона ReceiveAndSendReply
Шаблон **ReceiveAndSendReply** используется для создания пары предварительно настроенных и выполняемых <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> действий в рамках <xref:System.Activities.Statements.Sequence> действия, коррелированного как часть шаблона обмена сообщениями типа "запрос-ответ" на сервере.

## <a name="the-receiveandsendreply-template"></a>Шаблон ReceiveAndSendReply
 Добавление шаблона **ReceiveAndSendReply** делает три вещи, помимо создания <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> действий и с <xref:System.Activities.Statements.Sequence> действием:

1. Настраивает свойства <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Receive>.

2. Привязывает свойство <xref:System.ServiceModel.Activities.SendReply.Request%2A> действия <xref:System.ServiceModel.Activities.Receive> к действию <xref:System.ServiceModel.Activities.Send>.

3. Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="using-the-receiveandsendreply-template-designer"></a>Использование конструктора шаблонов ReceiveAndSendReply
 Конструктор действий **ReceiveAndSendReply** можно найти в категории **Обмен сообщениями** **области элементов**, щелкнув вкладку **область элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выбрать пункт **панель инструментов** в меню **вид** или нажав клавиши CTRL + ALT + X).

 Конструктор действий **ReceiveAndSendReply** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия. При этом создается <xref:System.ServiceModel.Activities.Receive> действие, которое можно настроить с помощью конструктора действий **отправки** , и коррелированный <xref:System.ServiceModel.Activities.SendReply> , который можно настроить с помощью конструктора SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)] сведения о настройке действия с помощью конструктора **получения** <xref:System.ServiceModel.Activities.Receive> см. в разделе [Получение](../workflow-designer/receive-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] сведения о настройке действия с помощью конструктора **SendReplyToReceive** <xref:System.ServiceModel.Activities.SendReply> см. в следующем разделе.

### <a name="properties-of-sendreply"></a>Свойства SendReply
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.SendReply> и описано их использование в конструкторе. These properties can be edited in properties grid and some can be edited on [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer surface.

|                               Имя свойства                                | Обязательно |                                                                                                                                                                                                                                                                                                                                                      Использование                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  Неверно   |                                                                                                                                                                                            Необязательное понятное имя действия <xref:System.ServiceModel.Activities.SendReply>. По умолчанию используется SendReplyToReceive.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Верно   | Ссылка на действие <xref:System.ServiceModel.Activities.Receive>, связанное с этим действием <xref:System.ServiceModel.Activities.SendReply>. Это свойство не может иметь **значение NULL**. <xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.SendReply>действия и используются совместно на сервере для моделирования шаблона обмена сообщениями "запрос-ответ". Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. Это свойство нельзя изменить в конструкторе, поскольку оно автоматически привязывается к действию <xref:System.ServiceModel.Activities.Send>, из которого было создано действие <xref:System.ServiceModel.Activities.SendReply>. |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  Неверно   |                       Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Измените это свойство, нажав кнопку с многоточием рядом с полем **содержимое** в сетке свойств или нажав кнопку **определить...** рядом с меткой **содержимое** в области конструктора действий **получения** . В обоих окнах отображается диалоговое окно **определения содержимого** . [!INCLUDE[crabout](../includes/crabout-md.md)] об использовании этого поля см. в разделе [диалогового окна «Определение содержимого](../workflow-designer/content-definition-dialog-box.md) ».                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  Неверно   |            Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом со <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> свойством в сетке свойства, чтобы открыть диалоговое окно **Добавление инициализаторов корреляции** . [!INCLUDE[crabout](../includes/crabout-md.md)] с помощью этого поля см. раздел [Добавление CorrelationInitializers в диалоговом окне](../workflow-designer/add-correlationinitializers-dialog-box.md) .            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  Неверно   |                                                                                                                                                                                                                                              Указывает заголовок действия сообщения. Если значение не задано явным образом, устанавливается значение по умолчанию:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  Неверно   |                                                                                                                                                                                                                                                                                          Указывает, нужно ли сохранять экземпляр рабочего процесса до отправки ответного сообщения. Значение по умолчанию — **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>См. также:
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)