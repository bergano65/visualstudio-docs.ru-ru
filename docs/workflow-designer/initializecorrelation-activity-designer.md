---
title: Конструктор рабочих процессов - конструктор действия InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496aefb2679edd87c892c54f44b14876b4ebce5b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953221"
---
# <a name="initializecorrelation-activity-designer"></a>Конструктор действия InitializeCorrelation

**InitializeCorrelation** конструктора действий используется для создания и настройки <xref:System.ServiceModel.Activities.InitializeCorrelation> действия. <xref:System.ServiceModel.Activities.InitializeCorrelation> Действие устанавливает корреляцию между сообщения перед их отправкой или получением.

## <a name="the-initializecorrelation-activity"></a>Действие InitializeCorrelation

Действие <xref:System.ServiceModel.Activities.InitializeCorrelation> используется для инициализации соотношений без отправки или получения сообщений. Обычно корреляция инициализируется при отправке или получении сообщения. Если корреляция должна быть установлена до отправки или получения сообщения, то для этого можно использовать <xref:System.ServiceModel.Activities.InitializeCorrelation>.

### <a name="using-the-initializecorrelation-activity-designer"></a>Использование конструктора действий InitializeCorrelation

Доступ **InitializeCorrelation** конструктора действий в **Messaging** категории **элементов**.

**InitializeCorrelation** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов. Удаление конструктора действий создает <xref:System.ServiceModel.Activities.InitializeCorrelation> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **InitializeCorrelation** конструктора действий или в **DisplayName** поле **свойства** окна.

<xref:System.ServiceModel.Activities.CorrelationHandle> Может быть указывает в **корреляции** в **свойства** окно на **InitializeCorrelation** рабочей области конструктора действий.

Для отображения **инициализация корреляции** диалоговое окно, где можно указать дескриптор взаимосвязи и пары ключ значение, используемое для инициализации, выберите кнопку с многоточием рядом с полем **CorrelationData** в поле **свойства** окна. Или выбрать текстом подсказки «Вид …» на **InitializeCorrelation** рабочей области конструктора действий. Дополнительные сведения об использовании это диалоговое окно, см. в разделе [диалоговое окно редактора коллекции типа](../workflow-designer/type-collection-editor-dialog-box.md) статьи.

### <a name="the-initializecorrelation-properties"></a>Свойства InitializeCorrelation

В следующей таблице показаны <xref:System.ServiceModel.Activities.InitializeCorrelation> свойства и показывается, как они используются в конструкторе. Эти свойства можно изменить в **свойства** окне или на поверхности конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>. По умолчанию используется InitializeCorrelation.<br /><br /> Несмотря на то что использование нестандартное значение для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, рекомендуется.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> используется для привязки действий рабочих процессов в корреляции.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Словарь данных корреляции привязывает сообщения к данному экземпляру рабочего потока.<br /><br /> Используйте **инициализация корреляции** диалоговое окно для настройки <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Дополнительные сведения об использовании это диалоговое окно, см. в разделе [диалоговое окно редактора коллекции типа](../workflow-designer/type-collection-editor-dialog-box.md) статьи.|

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)