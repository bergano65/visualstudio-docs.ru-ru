---
title: Конструктор действий блок-схемы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a85efea49d641fa54774c1428d15f7d8218ca53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656705"
---
# <a name="flowchart-activity-designer"></a>Конструктор действия блок-схемы
Действие <xref:System.Activities.Statements.Flowchart> служит для создания рабочих процессов, в которых определяются и поддерживаются сложные элементы управления потоком. <xref:System.Activities.Statements.Flowchart> можно создать в коде или с помощью [!INCLUDE[wfd2](../includes/wfd2-md.md)]. В этом разделе описана работа в [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Конструктор действия рабочего процесса [!INCLUDE[wfd1](../includes/wfd1-md.md)] позволяет разработчику создавать рабочие процессы естественным образом.

## <a name="the-flowchart-activity"></a>Действие Flowchart
 <xref:System.Activities.Statements.Flowchart> определяет уникальный <xref:System.Activities.Statements.Flowchart.StartNode%2A>, который выполняется при запуске рабочего процесса и использует сеть связанных <xref:System.Activities.Statements.Flowchart.Nodes%2A> для создания произвольных циклов или отклонения потока выполнения в любое место рабочего процесса в любой момент времени.

### <a name="using-the-flowchart-activity-designer"></a>Использование конструктора действия Flowchart
 Конструктор **действий блок-схемы** можно найти в категории **блок-схемы** **области элементов**, щелкнув вкладку **область элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выберите **панель инструментов** в меню **вид** или нажмите клавиши CTRL + ALT + X).

 Конструктор действий **блок-схемы** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где бы они ни находились, либо как корневое действие, либо как дочерний элемент другой операции потока управления. Если конструктор действий **блок-схемы** перемещается на пустую [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхность, он создает <xref:System.Activities.Statements.Flowchart> действие, которое по умолчанию представляет собой в развернутом представлении, в котором начальный узел, инициирующий выполнение, представляется зеленым шариком. Если конструктор действий **блок-схемы** перемещается в другую операцию потока управления, он представляется в режиме сворачивания, который можно расширить, дважды щелкнув конструктор действий **блок-схемы** . Любое действие на **панели элементов** можно перетащить непосредственно в конструктор действий **блок-схемы** , включая другие действия потока управления.

 После перетаскивания различных конструкторов действия на полотно [!INCLUDE[wfd2](../includes/wfd2-md.md)] объекты <xref:System.Activities.Activity>, которые они представляют, можно связать вместе или задать порядок их выполнения. Чтобы создать ссылку между исходным и целевым действием, поместите мышь над конструктором исходного действия, после чего на каждой его стороне появятся квадратные маркеры. Щелкните один из них и, удерживая нажатой кнопку мыши, перетащите его к одному из маркеров, которые аналогичным образом появляются на целевом действии при наведении мыши. Отпустите кнопку мыши, чтобы создать связь между этими двумя действиями, которая будет отмечена стрелкой от исходного к целевому конструктору.

### <a name="flowchart-activity-properties"></a>Свойства действия Flowchart
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Flowchart> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Указывает отображаемое имя конструктора действия в заголовке. По умолчанию используется Flowchart. Значение можно изменить в окне **Свойства** или непосредственно в заголовке конструктора действий.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Неверно|Коллекция переменных, доступных в этом <xref:System.Activities.Statements.Flowchart> для общего доступа к состоянию для вложенных действий.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Неверно|<xref:System.Activities.Statements.FlowNode>, который выполняется при запуске <xref:System.Activities.Statements.Flowchart>.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Неверно|Содержит коллекцию объектов <xref:System.Activities.Statements.FlowNode> в <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>См. также:
 [Блок-схема](../workflow-designer/flowchart-activity-designers.md) [FlowDecision](../workflow-designer/flowdecision-activity-designer.md) [FlowSwitch \<T> ](../workflow-designer/flowswitch-t-activity-designer.md)