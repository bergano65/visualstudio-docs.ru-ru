---
title: Конструктор рабочих процессов - конструктор действия Initializecorrelation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24d319af36b5d07661213edb3cff48d376bd3736
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977540"
---
# <a name="initializecorrelation-activity-designer"></a>Конструктор действия InitializeCorrelation

**InitializeCorrelation** конструктора действий используется для создания и настройки <xref:System.ServiceModel.Activities.InitializeCorrelation> действия, которое используется для соотнесения сообщений перед их отправкой или получением.

## <a name="the-initializecorrelation-activity"></a>Действие InitializeCorrelation

Действие <xref:System.ServiceModel.Activities.InitializeCorrelation> используется для инициализации соотношений без отправки или получения сообщений. Обычно корреляция инициализируется при отправке или получении сообщения. Если корреляция должна быть установлена до отправки или получения сообщения, то для этого можно использовать <xref:System.ServiceModel.Activities.InitializeCorrelation>.

### <a name="using-the-initializecorrelation-activity-designer"></a>Использование конструктора действий InitializeCorrelation
 **InitializeCorrelation** конструктора действий можно найти в **обмен сообщениями** категории **элементов**, который нажав **элементов**  вкладку в конструкторе рабочих процессов (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **InitializeCorrelation** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов. При этом создается <xref:System.ServiceModel.Activities.InitializeCorrelation> действия по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке **InitializeCorrelation** конструктора или в  **Отображаемое имя** поле **свойства** окна.

 <xref:System.ServiceModel.Activities.CorrelationHandle> Может быть указывает в **корреляции** в **свойства** окна на **InitializeCorrelation** области конструктора операций.

 Нажав кнопку с многоточием, помимо **CorrelationData** в **свойства** окна или текстом подсказки «Вид …» на **InitializeCorrelation** конструктора действий Отображает область **инициализация корреляции** диалоговое окно «», в котором можно указать дескриптор взаимосвязи и пары ключей и значений, используемых для инициализации его. Дополнительные сведения об этом диалоговом окне см. в разделе [диалоговое окно редактора коллекции типа](../workflow-designer/type-collection-editor-dialog-box.md) раздела.

### <a name="the-initializecorrelation-properties"></a>Свойства InitializeCorrelation
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.InitializeCorrelation> и описано их использование в конструкторе. Эти свойства можно изменить в **свойства** окне или на поверхности конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>. По умолчанию используется InitializeCorrelation.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> используется для привязки действий рабочих процессов в корреляции.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Словарь данных корреляции привязывает сообщения к данному экземпляру рабочего потока.<br /><br /> Используйте **инициализация корреляции** диалоговое окно используется для настройки <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Дополнительные сведения об использовании это диалоговое окно, в разделе [диалоговое окно редактора коллекции типа](../workflow-designer/type-collection-editor-dialog-box.md) раздела.|

## <a name="see-also"></a>См. также

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Отправить](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)