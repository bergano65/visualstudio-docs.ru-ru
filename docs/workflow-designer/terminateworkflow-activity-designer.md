---
title: "Конструктор действия Terminateworkflow | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e114f95baf771d8138fd155cf79f6e0ddbf14485
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="terminateworkflow-activity-designer"></a>Конструктор действия TerminateWorkflow
**TerminateWorkflow** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.TerminateWorkflow> действия.  
  
## <a name="the-terminateworkflow-activity"></a>Действие TerminateWorkflow  
 Действие <xref:System.Activities.Statements.TerminateWorkflow> прерывает выполнение текущего рабочего процесса.  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>Использование конструктора операций TerminateWorkflow  
 **TerminateWorkflow** конструктора действий можно найти в **среды выполнения** категории **элементов**, который нажав **элементов** вкладка (либо выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **TerminateWorkflow** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.TerminateWorkflow> действия по умолчанию **DisplayName** для TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **TerminateWorkflow** конструктора или в **DisplayName** поле сетки свойств.  
  
### <a name="the-terminateworkflow-properties"></a>Свойства TerminateWorkflow  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TerminateWorkflow> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.TerminateWorkflow>. Значение по умолчанию - TerminateWorkflow. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Исключение, которое будет создано при прерывании рабочего процесса. Задайте это свойство в таблице свойств.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Причина, которая объясняет причину прерывания рабочего процесса. Задайте это свойство в таблице свойств.|  
  
## <a name="see-also"></a>См. также  
 [Среда выполнения](../workflow-designer/runtime-activity-designers.md)   
 [Сохранение](../workflow-designer/persist-activity-designer.md)