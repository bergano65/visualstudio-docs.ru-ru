---
title: Конструктор действий конструктор рабочих процессов InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650227"
---
# <a name="initializecorrelation-activity-designer"></a>Конструктор действия InitializeCorrelation

Конструктор действий **InitializeCorrelation** используется для создания и настройки действия <xref:System.ServiceModel.Activities.InitializeCorrelation>. Действие <xref:System.ServiceModel.Activities.InitializeCorrelation> устанавливает корреляцию между сообщениями перед их отправкой или получением.

## <a name="the-initializecorrelation-activity"></a>Действие InitializeCorrelation

Действие <xref:System.ServiceModel.Activities.InitializeCorrelation> используется для инициализации соотношений без отправки или получения сообщений. Обычно корреляция инициализируется при отправке или получении сообщения. Если корреляция должна быть установлена до отправки или получения сообщения, то для этого можно использовать <xref:System.ServiceModel.Activities.InitializeCorrelation>.

### <a name="using-the-initializecorrelation-activity-designer"></a>Использование конструктора действий InitializeCorrelation

Доступ к конструктору действий **InitializeCorrelation** в категории **обмена сообщениями** **панели элементов**.

Конструктор действий **InitializeCorrelation** можно перетащить из **области элементов** в область Конструктор рабочих процессов. При удалении конструктора действий создается <xref:System.ServiceModel.Activities.InitializeCorrelation> действие с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию InitializeCorrelation. @No__t_0 можно изменить в заголовке конструктора действий **InitializeCorrelation** или в поле **DisplayName** окна **Свойства** .

@No__t_0 можно указать в поле " **корреляция** " в окне " **свойства** " в области конструктора действий **InitializeCorrelation** .

Чтобы открыть диалоговое окно " **Инициализация корреляции** ", в котором можно указать маркер корреляции и пары "ключ-значение", используемые для его инициализации, нажмите кнопку с многоточием рядом с полем **CorrelationData** в окне " **Свойства** ". Или выберите "View..." (Просмотр...) текст подсказки на поверхности конструктора действий **InitializeCorrelation** . Дополнительные сведения об использовании этого диалогового окна см. в статье [диалоговое окно Редактор коллекции типов](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Свойства InitializeCorrelation

В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.InitializeCorrelation> и описано, как они используются в конструкторе. Эти свойства можно изменять в окне " **Свойства** " или на конструктор рабочих процессов поверхности.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>. По умолчанию используется InitializeCorrelation.<br /><br /> Хотя использование значения, отличного от используемого по умолчанию, для понятного <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, рекомендуется.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> используется для привязки действий рабочих процессов в корреляции.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Словарь данных корреляции привязывает сообщения к данному экземпляру рабочего потока.<br /><br /> Используйте диалоговое окно " **Инициализация корреляции** " для настройки <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Дополнительные сведения об использовании этого диалогового окна см. в статье [диалоговое окно Редактор коллекции типов](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)