---
title: Конструктор действия CorrelationScope | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 95c8422d53903c3c7b81db9f6ef042c5ea9ff1c1
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "58990054"
---
# <a name="correlationscope-activity-designer"></a>Конструктор действия CorrelationScope
**CorrelationScope** конструктора действий используется для создания и настройки <xref:System.ServiceModel.Activities.CorrelationScope> действие, которое обеспечивает неявное управление дочерними действиями обмена сообщениями с помощью <xref:System.ServiceModel.Activities.CorrelationHandle> объекта.  
  
## <a name="the-correlationscope-activity"></a>Действие CorrelationScope  
 Свойство <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщениями. Действия <xref:System.ServiceModel.Activities.Send> и <xref:System.ServiceModel.Activities.Receive>, содержащиеся в свойстве <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>, настроены на использование свойства <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> содержащегося действия <xref:System.ServiceModel.Activities.CorrelationScope> для выполнения корреляции.  
  
### <a name="using-the-correlationscope-activity-designer"></a>Использование конструктора операций CorrelationScope  
 **CorrelationScope** конструктора действий можно найти в **Messaging** категории **элементов**, который нажав **панелиэлементов** вкладка в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **CorrelationScope** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности. При этом создается <xref:System.ServiceModel.Activities.CorrelationScope> действие по умолчанию **DisplayName** для CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **CorrelationScope** конструктора действий или в **DisplayName** поле **свойства** окна.  
  
 Чтобы указать <xref:System.ServiceModel.Activities.CorrelationHandle> используемый дочерними действиями обмена сообщениями, нажмите кнопку с многоточием рядом с **CorrelatesWith** в **свойства** окно для отображения **редактор выражений**  диалоговое окно. Это свойство также можно задать в области конструктора операций.  
  
 Действия, ограниченные пределами корреляции, указываются путем сброса их конструкторов в **текст** поле в пределах **CorrelationScope** конструктора.  
  
### <a name="the-correlationscope-properties"></a>Свойства CorrelationScope  
 В следующей таблице показаны свойства <xref:System.ServiceModel.Activities.CorrelationScope> и описано их использование в конструкторе. Эти свойства можно изменить либо в **свойства** окне или на [!INCLUDE[wfd2](../includes/wfd2-md.md)] конструктора и часто в обеих.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.ServiceModel.Activities.InitializeCorrelation>.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Задает объект <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для управления дочерними действиями обмена сообщений. Если это свойство не задано, то действие <xref:System.ServiceModel.Activities.CorrelationScope> создает неявный объект <xref:System.ServiceModel.Activities.CorrelationHandle> автоматически.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Указывает действия в области корреляции.|  
  
## <a name="see-also"></a>См. также  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Получение](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Отправить](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)