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
ms.openlocfilehash: 4ecb0e201c4351a8a117d1e35aca97866b2beb89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663272"
---
# <a name="sendandreceivereply-template-designer"></a>Конструктор шаблона SendAndReceiveReply
Шаблон **SendAndReceiveReply** используется для создания пары предварительно настроенных <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> действий в <xref:System.Activities.Statements.Sequence> действии, которые сопоставлены как часть шаблона обмена сообщениями типа "запрос-ответ" на клиенте.

## <a name="the-sendandreceivereply-template"></a>Шаблон SendAndReceiveReply
 Добавление шаблона **SendAndReceiveReply** делает три вещи, помимо создания <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> действий в рамках <xref:System.Activities.Statements.Sequence> действия.

1. Настраивает свойства <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> действия <xref:System.ServiceModel.Activities.Send>.

2. Привязывает свойство <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> действия <xref:System.ServiceModel.Activities.ReceiveReply> к действию <xref:System.ServiceModel.Activities.Send>.

3. Создает <xref:System.ServiceModel.Activities.CorrelationHandle> в качестве переменной в родительском действии.

### <a name="using-the-sendandreceivereply-template-designer"></a>Использование конструктора шаблонов SendAndReceiveReply
 Конструктор действий **SendAndReceiveReply** можно найти в категории **Обмен сообщениями** **панели элементов**, щелкнув вкладку **область элементов** на [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** из **представления** . меню или CTRL + ALT + X.)

 Конструктор действий **SendAndReceiveReply** можно перетащить из **панели элементов** в область [!INCLUDE[wfd2](../includes/wfd2-md.md)], где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Send>, которое можно настроить с помощью конструктора действий **отправки** , и коррелированные <xref:System.ServiceModel.Activities.ReceiveReply>, которые можно настроить с помощью конструктора **рецеивереплифорсенд** .

 [!INCLUDE[crabout](../includes/crabout-md.md)] использовании конструктора **отправки** для настройки действия <xref:System.ServiceModel.Activities.Send> см. в разделе [Отправка](../workflow-designer/send-activity-designer.md) статьи.

 [!INCLUDE[crabout](../includes/crabout-md.md)] использовании конструктора **рецеивереплифорсенд** для настройки действия <xref:System.ServiceModel.Activities.ReceiveReply> см. в следующем разделе.

### <a name="properties-of-receivereply"></a>Свойства ReceiveReply
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.ReceiveReply> и описано их использование в конструкторе. These properties can be edited in properties grid and some can be edited on [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer surface.

|                                 Имя свойства                                 | Обязательное значение |                                                                                                                                                                                                                                                                                                                                                        Использование                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            Необязательное понятное имя действия <xref:System.ServiceModel.Activities.ReceiveReply>. По умолчанию - ReceiveReplyForSend.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Ссылка на действие <xref:System.ServiceModel.Activities.Send>, связанное с этим действием <xref:System.ServiceModel.Activities.ReceiveReply>. Это свойство не может иметь **значение NULL**. Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.ReceiveReply> используются совместно на клиенте для моделирования обмена сообщениями по принципу «запрос–ответ». Это свойство указывает сопоставленное действие <xref:System.ServiceModel.Activities.Send>. Это свойство нельзя изменить в конструкторе, поскольку оно автоматически привязывается к действию <xref:System.ServiceModel.Activities.Send>, из которого было создано действие <xref:System.ServiceModel.Activities.ReceiveReply>. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Указывает получаемое содержимое сообщения или параметра. Это может быть либо действие <xref:System.ServiceModel.Activities.ReceiveMessageContent>, либо действие <xref:System.ServiceModel.Activities.ReceiveParametersContent>. Измените это свойство, нажав кнопку с многоточием рядом с полем **содержимое** в сетке свойств или нажав кнопку **определить...** рядом с меткой **содержимое** в области конструктора действий **получения** . В обоих окнах отображается диалоговое окно **определения содержимого** . [!INCLUDE[crabout](../includes/crabout-md.md)] использовании этого поля см. в разделе [диалогового окна «Определение содержимого](../workflow-designer/content-definition-dialog-box.md) ».                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Указывает коллекцию объектов <xref:System.ServiceModel.Activities.CorrelationInitializer>, инициализирующих несколько объектов <xref:System.ServiceModel.Activities.CorrelationHandle>, которые настраивают это действие <xref:System.ServiceModel.Activities.Receive> в рамках рабочего процесса. Нажмите кнопку с многоточием рядом со свойством <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> в сетке свойств, чтобы открыть диалоговое окно **Добавление инициализаторов корреляции** . [!INCLUDE[crabout](../includes/crabout-md.md)] использовании этого поля см. в разделе, посвященном [диалоговому окну Add CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Указывает заголовок действия сообщения. Если значение не задано явным образом, устанавливается значение по умолчанию:<br /><br /> <strong>https://tempuri.org/{service пространство имен контракта}/{сервице имя контракта} имя/{Оператион}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>См. также раздел
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Получение](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)