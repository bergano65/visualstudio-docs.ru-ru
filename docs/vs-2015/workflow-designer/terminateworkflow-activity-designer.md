---
title: Конструктор действия TerminateWorkflow | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: a00677390967f0cc0cff8a04b33895d7c88588f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568763"
---
# <a name="terminateworkflow-activity-designer"></a>Конструктор действия TerminateWorkflow
**TerminateWorkflow** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.TerminateWorkflow> действия.  
  
## <a name="the-terminateworkflow-activity"></a>Действие TerminateWorkflow  
 Действие <xref:System.Activities.Statements.TerminateWorkflow> прерывает выполнение текущего рабочего процесса.  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>Использование конструктора операций TerminateWorkflow  
 **TerminateWorkflow** конструктора действий можно найти в **среды выполнения** категории **элементов**, который нажав **панелиэлементов** вкладка (Кроме того, выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **TerminateWorkflow** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.TerminateWorkflow> действие по умолчанию **DisplayName** для TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **TerminateWorkflow** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-terminateworkflow-properties"></a>Свойства TerminateWorkflow  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TerminateWorkflow> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.TerminateWorkflow>. Значение по умолчанию - TerminateWorkflow. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Исключение, которое будет создано при прерывании рабочего процесса. Задайте это свойство в таблице свойств.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Причина, которая объясняет причину прерывания рабочего процесса. Задайте это свойство в таблице свойств.|  
  
## <a name="see-also"></a>См. также  
 [Среда выполнения](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)