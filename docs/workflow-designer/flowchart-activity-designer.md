---
title: Конструктор рабочих процессов - конструктор действия блок-схемы
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81af4a51da2bb15bafd17fc7ba98d676f7b0decc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="flowchart-activity-designer"></a>Конструктор действия блок-схемы

Действие <xref:System.Activities.Statements.Flowchart> служит для создания рабочих процессов, в которых определяются и поддерживаются сложные элементы управления потоком. Объект <xref:System.Activities.Statements.Flowchart> может быть создано в коде или с помощью конструктора рабочих процессов. В этом разделе описываются возможности конструктора рабочих процессов. Конструктора действий рабочего процесса конструктора рабочих процессов Windows позволяет разработчику создавать рабочие процессы естественным образом.

## <a name="the-flowchart-activity"></a>Действие Flowchart

<xref:System.Activities.Statements.Flowchart> определяет уникальный <xref:System.Activities.Statements.Flowchart.StartNode%2A>, который выполняется при запуске рабочего процесса и использует сеть связанных <xref:System.Activities.Statements.Flowchart.Nodes%2A> для создания произвольных циклов или отклонения потока выполнения в любое место рабочего процесса в любой момент времени.

### <a name="using-the-flowchart-activity-designer"></a>Использование конструктора действия Flowchart

**Блок-схема** конструктора действий можно найти в **блок-схема** категории **элементов**, который нажав **элементов**вкладку в конструкторе рабочих процессов (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

**Блок-схема** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно помещаются конструкторы, в качестве корневого действия или дочерний другое действие потока управления. Если **блок-схема** перетащить конструктор действия в пустую область конструктора рабочих процессов, он создает <xref:System.Activities.Statements.Flowchart> действие, которое по умолчанию представлено в развернутом виде, в котором находится начальный узел, инициирующий выполнение представлен зеленым кружком. Если **блок-схема** перетащить конструктор действия на другое действие потока управления, то он показывается в свернутом виде, который можно развернуть двойным щелчком **блок-схема** конструктора действий. Любое действие в **элементов** можно перетащить напрямую в **блок-схема** конструктора действий, включая другие действия потока управления.

После перетаскивания различных конструкторов действия на полотно конструктора рабочих процессов, <xref:System.Activities.Activity> они представляют объекты могут быть связаны друг с другом, чтобы указать порядок выполнения. Чтобы создать ссылку между исходным и целевым действием, поместите мышь над конструктором исходного действия, после чего на каждой его стороне появятся квадратные маркеры. Щелкните один из них и, удерживая нажатой кнопку мыши, перетащите его к одному из маркеров, которые аналогичным образом появляются на целевом действии при наведении мыши. Отпустите кнопку мыши, чтобы создать связь между этими двумя действиями, которая будет отмечена стрелкой от исходного к целевому конструктору.

### <a name="flowchart-activity-properties"></a>Свойства действия Flowchart

В следующей таблице показаны свойства <xref:System.Activities.Statements.Flowchart> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает отображаемое имя конструктора действия в заголовке. По умолчанию используется Flowchart. Значение можно изменить в **свойства** окна или напрямую в заголовке конструктора действий.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Коллекция переменных, доступных в этом <xref:System.Activities.Statements.Flowchart> для общего доступа к состоянию для вложенных действий.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode>, который выполняется при запуске <xref:System.Activities.Statements.Flowchart>.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Содержит коллекцию объектов <xref:System.Activities.Statements.FlowNode> в <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>См. также

- [Блок-схема](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)