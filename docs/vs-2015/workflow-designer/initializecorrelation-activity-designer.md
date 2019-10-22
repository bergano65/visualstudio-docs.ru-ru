---
title: Конструктор действий InitializeCorrelation | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659019"
---
# <a name="initializecorrelation-activity-designer"></a>Конструктор действия InitializeCorrelation
Конструктор действий **InitializeCorrelation** используется для создания и настройки действия <xref:System.ServiceModel.Activities.InitializeCorrelation>, которое используется для установления корреляции между сообщениями перед их отправкой или получением.

## <a name="the-initializecorrelation-activity"></a>Действие InitializeCorrelation
 Действие <xref:System.ServiceModel.Activities.InitializeCorrelation> используется для инициализации соотношений без отправки или получения сообщений. Обычно корреляция инициализируется при отправке или получении сообщения. Если корреляция должна быть установлена до отправки или получения сообщения, то для этого можно использовать <xref:System.ServiceModel.Activities.InitializeCorrelation>.

### <a name="using-the-initializecorrelation-activity-designer"></a>Использование конструктора действий InitializeCorrelation
 Конструктор действий **InitializeCorrelation** можно найти в категории **Обмен сообщениями** **области элементов**, щелкнув вкладку **область элементов** на [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выбрать **панель инструментов** из представления).меню или CTRL + ALT + X.)

 Конструктор действий **InitializeCorrelation** можно перетащить из **области элементов** в область [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Будет создано действие <xref:System.ServiceModel.Activities.InitializeCorrelation> с <xref:System.Activities.Activity.DisplayName%2A>ом по умолчанию InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действий **InitializeCorrelation** или в поле **DisplayName** окна **свойств** .

 @No__t_0 можно указать в поле " **корреляция** " в окне " **свойства** " в области конструктора действий **InitializeCorrelation** .

 Нажмите кнопку с многоточием, кроме поля **CorrelationData** в окне " **Свойства** " или "View..." текст подсказки в области конструктора действий **InitializeCorrelation** отображает диалоговое окно " **Инициализация корреляции** ", в котором можно указать маркер корреляции и пары "ключ-значение", используемые для его инициализации. [!INCLUDE[crabout](../includes/crabout-md.md)] использовании этого диалогового окна см. в разделе [диалоговое окно Редактор коллекции типов](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Свойства InitializeCorrelation
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.InitializeCorrelation> и описано их использование в конструкторе. Эти свойства можно изменять в окне " **Свойства** " или на [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>. По умолчанию используется InitializeCorrelation.<br /><br /> Несмотря на то, что использовать значение, отличное от значения по умолчанию, для понятного имени <xref:System.Activities.Activity.DisplayName%2A> не требуется, его все же рекомендуется использовать.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> используется для привязки действий рабочих процессов в корреляции.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Словарь данных корреляции привязывает сообщения к данному экземпляру рабочего потока.<br /><br /> Используйте диалоговое окно " **Инициализация корреляции** " для настройки <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] диалоговом окне использование этого диалогового окна см. в разделе [диалоговое окно Редактор коллекции типов](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>См. также раздел
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)