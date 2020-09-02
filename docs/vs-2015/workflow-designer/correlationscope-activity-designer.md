---
title: Конструктор действий CorrelationScope | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ffcfd63d60ab6f085b5cb2a793e8bf17a50d8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656910"
---
# <a name="correlationscope-activity-designer"></a>Конструктор действия CorrelationScope
Конструктор действий **CorrelationScope** используется для создания и настройки <xref:System.ServiceModel.Activities.CorrelationScope> действия, которое обеспечивает неявное Управление дочерними операциями обмена сообщениями с помощью <xref:System.ServiceModel.Activities.CorrelationHandle> объекта.

## <a name="the-correlationscope-activity"></a>Действие CorrelationScope
 Свойство <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщениями. Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.Receive>, содержащиеся в свойстве <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>, настроены на использование свойства <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> содержащегося действия <xref:System.ServiceModel.Activities.CorrelationScope> для выполнения корреляции.

### <a name="using-the-correlationscope-activity-designer"></a>Использование конструктора операций CorrelationScope
 Конструктор действий **CorrelationScope** можно найти в категории **Обмен сообщениями** **панели элементов**, щелкнув вкладку **область элементов** в левой части окна [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать пункт **панель инструментов** в меню **вид** или CTRL + ALT + X).

 Конструктор действий **CorrelationScope** можно перетащить из **области элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область. При этом создается <xref:System.ServiceModel.Activities.CorrelationScope> действие со значением **DisplayName** по умолчанию CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **CorrelationScope** или в поле **DisplayName** окна **Свойства** .

 Чтобы указать, <xref:System.ServiceModel.Activities.CorrelationHandle> используемое дочерними действиями обмена сообщениями, нажмите кнопку с многоточием рядом с полем **CorrelatesWith** в окне " **Свойства** ", чтобы открыть диалоговое окно **Редактор выражений** . Это свойство также можно задать в области конструктора операций.

 Действия, заданные в рамках корреляции, задаются путем удаления их конструкторов в поле **Body** в конструкторе **CorrelationScope** .

### <a name="the-correlationscope-properties"></a>Свойства CorrelationScope
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.CorrelationScope> и описано их использование в конструкторе. Эти свойства можно изменять либо в окне « **Свойства** », либо в [!INCLUDE[wfd2](../includes/wfd2-md.md)] области конструктора, и часто в обоих случаях.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Неверно|Задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщений. Если это свойство не задано, то действие <xref:System.ServiceModel.Activities.CorrelationScope> создает неявный объект <xref:System.ServiceModel.Activities.CorrelationHandle> автоматически.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Неверно|Указывает действия в области корреляции.|

## <a name="see-also"></a>См. также:
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)