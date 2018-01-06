---
title: "Конструктор действия блок-схема | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d8bcdcc42ada14f808c165e9e06b269817f79575
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="flowchart-activity-designer"></a>Конструктор действия блок-схемы
Действие <xref:System.Activities.Statements.Flowchart> служит для создания рабочих процессов, в которых определяются и поддерживаются сложные элементы управления потоком. <xref:System.Activities.Statements.Flowchart> можно создать в коде или с помощью [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. В этом разделе описана работа в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Конструктор действия рабочего процесса [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] позволяет разработчику создавать рабочие процессы естественным образом.  
  
## <a name="the-flowchart-activity"></a>Действие Flowchart  
 <xref:System.Activities.Statements.Flowchart> определяет уникальный <xref:System.Activities.Statements.Flowchart.StartNode%2A>, который выполняется при запуске рабочего процесса и использует сеть связанных <xref:System.Activities.Statements.Flowchart.Nodes%2A> для создания произвольных циклов или отклонения потока выполнения в любое место рабочего процесса в любой момент времени.  
  
### <a name="using-the-flowchart-activity-designer"></a>Использование конструктора действия Flowchart  
 **Блок-схема** конструктора действий можно найти в **блок-схема** категории **элементов**, который нажав **элементов**вкладки [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Блок-схема** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно помещаются конструкторы, как корневого действия или дочернего другого действия потока управления. Если **блок-схема** перетащить конструктор действия в пустую [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности, он создает <xref:System.Activities.Statements.Flowchart> действие, которое по умолчанию представлено в развернутом виде, в котором находится начальный узел, инициирующий выполнение представлен зеленым кружком. Если **блок-схема** перетащить конструктор действия на другое действие потока управления, то он показывается в свернутом виде, который можно развернуть двойным щелчком **блок-схема** конструктора действий. Любое действие в **элементов** можно перетащить напрямую в **блок-схема** конструктора действий, включая другие действия потока управления.  
  
 После перетаскивания различных конструкторов действия на полотно [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] объекты <xref:System.Activities.Activity>, которые они представляют, можно связать вместе или задать порядок их выполнения. Чтобы создать ссылку между исходным и целевым действием, поместите мышь над конструктором исходного действия, после чего на каждой его стороне появятся квадратные маркеры. Щелкните один из них и, удерживая нажатой кнопку мыши, перетащите его к одному из маркеров, которые аналогичным образом появляются на целевом действии при наведении мыши. Отпустите кнопку мыши, чтобы создать связь между этими двумя действиями, которая будет отмечена стрелкой от исходного к целевому конструктору.  
  
### <a name="flowchart-activity-properties"></a>Свойства действия Flowchart  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Flowchart> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает отображаемое имя конструктора действия в заголовке. По умолчанию используется Flowchart. Значение можно изменить в **свойства** окна или напрямую в заголовке конструктора действий.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Коллекция переменных, доступных в этом <xref:System.Activities.Statements.Flowchart> для общего доступа к состоянию для вложенных действий.|  
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode>, который выполняется при запуске <xref:System.Activities.Statements.Flowchart>.|  
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Содержит коллекцию объектов <xref:System.Activities.Statements.FlowNode> в <xref:System.Activities.Statements.Flowchart>.|  
  
## <a name="see-also"></a>См. также  
 [Блок-схемы](../workflow-designer/flowchart-activity-designers.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)   
 [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)