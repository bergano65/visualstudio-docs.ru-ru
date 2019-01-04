---
title: Конструктор рабочих процессов - конструктор действия CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0562b113e91bb9485eaf356085715522b1b39bc3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829924"
---
# <a name="correlationscope-activity-designer"></a>Конструктор действия CorrelationScope

**CorrelationScope** конструктора действий используется для создания и настройки <xref:System.ServiceModel.Activities.CorrelationScope> действие, которое обеспечивает неявное управление дочерними действиями обмена сообщениями с помощью <xref:System.ServiceModel.Activities.CorrelationHandle> объекта.

## <a name="the-correlationscope-activity"></a>Действие CorrelationScope

Свойство <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщениями. Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.Receive>, содержащиеся в свойстве <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>, настроены на использование свойства <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> содержащегося действия <xref:System.ServiceModel.Activities.CorrelationScope> для выполнения корреляции.

### <a name="use-the-correlationscope-activity-designer"></a>Использование конструктора операций CorrelationScope

**CorrelationScope** конструктора действий можно найти в **Messaging** категории **элементов**, который нажав **панелиэлементов** вкладка в левой части конструктора рабочих процессов. Можно также выбрать **элементов** из **представление** меню или нажмите клавишу **Ctrl**+**Alt** + **X**.

**CorrelationScope** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов. При этом создается <xref:System.ServiceModel.Activities.CorrelationScope> действие по умолчанию **DisplayName** для CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **CorrelationScope** конструктора действий или в **DisplayName** поле **свойства** окна.

Чтобы указать <xref:System.ServiceModel.Activities.CorrelationHandle> используемый дочерними действиями обмена сообщениями, выберите кнопку с многоточием рядом с **CorrelatesWith** в **свойства** окно для отображения **выражение Редактор** диалоговое окно. Это свойство также можно задать в области конструктора операций.

Действия, ограниченные пределами корреляции, указываются путем сброса их конструкторов в **текст** поле в пределах **CorrelationScope** конструктора.

### <a name="the-correlationscope-properties"></a>Свойства CorrelationScope

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.CorrelationScope> и описано их использование в конструкторе. Эти свойства можно изменить либо в **свойства** окно или в рабочей области конструктора рабочих процессов и часто в обеих.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщений. Если это свойство не задано, то действие <xref:System.ServiceModel.Activities.CorrelationScope> создает неявный объект <xref:System.ServiceModel.Activities.CorrelationHandle> автоматически.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Указывает действия в области корреляции.|

## <a name="see-also"></a>См. также

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)