---
title: Конструктор действия Correlationscope | Документы Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63d429d0196283795a6d034bc5f1a0c72773ff42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="correlationscope-activity-designer"></a>Конструктор действия CorrelationScope
**CorrelationScope** конструктора действий используется для создания и настройки <xref:System.ServiceModel.Activities.CorrelationScope> действия, которое обеспечивает неявное управление дочерними действиями обмена сообщениями с помощью <xref:System.ServiceModel.Activities.CorrelationHandle> объекта.

## <a name="the-correlationscope-activity"></a>Действие CorrelationScope
 Свойство <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщениями. Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.Receive>, содержащиеся в свойстве <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>, настроены на использование свойства <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> содержащегося действия <xref:System.ServiceModel.Activities.CorrelationScope> для выполнения корреляции.

### <a name="using-the-correlationscope-activity-designer"></a>Использование конструктора операций CorrelationScope
 **CorrelationScope** конструктора действий можно найти в **обмен сообщениями** категории **элементов**, который нажав **элементов** вкладка на левой стороне [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **CorrelationScope** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности. При этом создается <xref:System.ServiceModel.Activities.CorrelationScope> действия по умолчанию **DisplayName** для CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **CorrelationScope** конструктора или в **DisplayName** поле **свойства** окна.

 Чтобы указать <xref:System.ServiceModel.Activities.CorrelationHandle> используемый дочерними действиями обмена сообщениями, нажмите кнопку с многоточием рядом с **CorrelatesWith** в **свойства** окно для отображения **редактор выражений ** диалоговое окно. Это свойство также можно задать в области конструктора операций.

 Действия, ограниченные пределами корреляции, указываются путем сброса их конструкторов в **текст** внутри **CorrelationScope** конструктора.

### <a name="the-correlationscope-properties"></a>Свойства CorrelationScope
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.CorrelationScope> и описано их использование в конструкторе. Эти свойства можно изменить либо в **свойства** окне или на [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] конструктор конструктора и часто в обеих.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщений. Если это свойство не задано, то действие <xref:System.ServiceModel.Activities.CorrelationScope> создает неявный объект <xref:System.ServiceModel.Activities.CorrelationHandle> автоматически.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Указывает действия в области корреляции.|

## <a name="see-also"></a>См. также

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)