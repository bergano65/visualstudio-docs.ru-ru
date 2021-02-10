---
title: Конструктор действий конструктор рабочих процессов CorrelationScope
description: Узнайте, как можно использовать конструктор действий CorrelationScope для создания и настройки действия CorrelationScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9edd755465cf812c1572c62f1c6335fc5295281
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955529"
---
# <a name="correlationscope-activity-designer"></a>Конструктор действия CorrelationScope

Конструктор действий **CorrelationScope** используется для создания и настройки <xref:System.ServiceModel.Activities.CorrelationScope> действия, которое обеспечивает неявное Управление дочерними операциями обмена сообщениями с помощью <xref:System.ServiceModel.Activities.CorrelationHandle> объекта.

## <a name="the-correlationscope-activity"></a>Действие CorrelationScope

Свойство <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщениями. Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.Receive>, содержащиеся в свойстве <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>, настроены на использование свойства <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> содержащегося действия <xref:System.ServiceModel.Activities.CorrelationScope> для выполнения корреляции.

### <a name="use-the-correlationscope-activity-designer"></a>Использование конструктора действий CorrelationScope

Конструктор действий **CorrelationScope** можно найти в категории **Обмен сообщениями** **области элементов**, щелкнув вкладку **область элементов** в левой части конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

Конструктор действий **CorrelationScope** можно перетащить из **области элементов** в область Конструктор рабочих процессов. При этом создается <xref:System.ServiceModel.Activities.CorrelationScope> действие со значением **DisplayName** по умолчанию CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **CorrelationScope** или в поле **DisplayName** окна **Свойства** .

Чтобы указать, <xref:System.ServiceModel.Activities.CorrelationHandle> используемое дочерними операциями обмена сообщениями, нажмите кнопку с многоточием рядом с полем **CorrelatesWith** в окне " **Свойства** ", чтобы открыть диалоговое окно **Редактор выражений** . Это свойство также можно задать в области конструктора операций.

Действия, заданные в рамках корреляции, задаются путем удаления их конструкторов в поле **Body** в конструкторе **CorrelationScope** .

### <a name="the-correlationscope-properties"></a>Свойства CorrelationScope

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.CorrelationScope> и описано их использование в конструкторе. Эти свойства можно изменять либо в окне « **Свойства** », либо на поверхности конструктор рабочих процессов и часто в обоих.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщений. Если это свойство не задано, то действие <xref:System.ServiceModel.Activities.CorrelationScope> создает неявный объект <xref:System.ServiceModel.Activities.CorrelationHandle> автоматически.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Указывает действия в области корреляции.|

## <a name="see-also"></a>См. также раздел

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Получать](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)