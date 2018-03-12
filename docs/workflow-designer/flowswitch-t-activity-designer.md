---
title: "FlowSwitch&lt;T&gt; конструктора | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 791067ff7e29a3eb63fd77e81a692f93edbda535
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt; конструктора действий
Действие <xref:System.Activities.Statements.FlowSwitch%601> - это условный узел, который обеспечивает ветвление потока управления на основе критерия соответствия, когда требуется более двух альтернативных ветвей. Если ветвление потока требует наличие только двух ветвей, вместо этого следует использовать действие <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>FlowSwitch < T\> действия
 <xref:System.Activities.Statements.FlowSwitch%601> Действие содержит <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , возвращающий значение типа *T* (указанный в универсальном параметре) при вычислении. Действие также содержит набор <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, который задает уникальное сопоставление на основе возможных результатов данного вычисления набору объектов <xref:System.Activities.Statements.FlowNode>. <xref:System.Activities.Statements.FlowNode> Выполнения является один из объектов типа *T* совпадает со значением вычисленного <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Вариант <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> может быть (дополнительно) предоставлен для варианта, в котором совпадений не было.

### <a name="using-the-flowswitcht-activity-designer"></a>С помощью FlowSwitch\<T > конструктора действий
 **FlowSwitch\<T >** конструктора действий можно найти в **блок-схема** категории **элементов**, который нажав **Элементов** вкладка на левой стороне [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

 **FlowSwitch\<T >** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] внутри конструктора **блок-схема** Конструктор операций. Используйте **Выбор типов** окно, отображающее для указания типа (связанного в коде с <xref:System.Activities.Statements.FlowSwitch%601> с помощью его общего параметра) полученного от вычисления <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Данная процедура создает <xref:System.Activities.Statements.FlowSwitch%601> действие **коммутатор** в <xref:System.Activities.Statements.Flowchart> действия. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Можно ввести в **выражение** поле **свойства** окно, нажав кнопку, где написано «Введите выражение VB».

 Наведите указатель мыши **FlowSwitch\<T >** конструктора действий, чтобы квадратных маркеров, которые используются для связи <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> для отображения вокруг его границ. После перетаскивания **FlowSwitch < T\>**  конструктора действий и других конструкторов в область **блок-схема**, <xref:System.Activities.Activity> объекты, которые они представляют, можно связать друг с другом Чтобы указать порядок выполнения. Для создания одного из <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> связанных с <xref:System.Activities.Statements.FlowSwitch%601>, выберите один из квадратных маркеров по периметру **FlowSwitch < T\>**  и перетащите его (удерживая кнопку мыши) на один из маркеров При наведении указателя мыши на его конструктор, которая отображается аналогичным образом вокруг целевого действия. Отпустите кнопку мыши, а стрелку от **FlowSwitch < T\>**  к целевому конструктору отображается, представляющему данный вариант. Значение по умолчанию для данного варианта отображается на стрелке и могут редактироваться в **случай** поле **свойства** окна.

### <a name="the-flowswitcht-properties"></a>FlowSwitch < T\> свойства
 В следующей таблице показаны свойства <xref:System.Activities.Statements.FlowSwitch%601> и описано их использование в конструкторе. Эти свойства можно изменить в сетке свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Указывает выражение, вычисляемое для определения того, на какой из вариантов <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> следует переключиться в пути выполнения.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Задает уникальное сопоставление возможных результатов, полученных при вычислении <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, набору объектов <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Задает сопоставление, когда вычисление <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> не совпадает ни с одним значением, содержащимся в объекте <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>См. также

- [Блок-схема](../workflow-designer/flowchart-activity-designers.md)
- [Блок-схема](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)