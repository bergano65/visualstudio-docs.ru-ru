---
title: Конструктор действий конструктор рабочих процессов-FlowSwitch <T>
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f167f46a2ed118e8781f66e4a781d4a3ef95b0d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650409"
---
# <a name="flowswitcht-activity-designer"></a>Конструктор действий > FlowSwitch \<T

Действие <xref:System.Activities.Statements.FlowSwitch%601> - это условный узел, который обеспечивает ветвление потока управления на основе критерия соответствия, когда требуется более двух альтернативных ветвей. Если ветвление потока требует наличие только двух ветвей, вместо этого следует использовать действие <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>Действие FlowSwitch \<T >

@No__t_0 действие содержит <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, который возвращает значение типа *t* (заданное универсальным параметром) при вычислении. Действие также содержит набор <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, который задает уникальное сопоставление на основе возможных результатов данного вычисления набору объектов <xref:System.Activities.Statements.FlowNode>. @No__t_0 выполняется, объект типа *t* которого соответствует значению вычисляемого <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Вариант <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> может быть (дополнительно) предоставлен для варианта, в котором совпадений не было.

### <a name="using-the-flowswitcht-activity-designer"></a>Использование конструктора действий > FlowSwitch \<T

Конструктор действий **FlowSwitch \<T >** можно найти в категории блок- **схема** **области элементов**, щелкнув вкладку **область элементов** в левой части конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** +**ALT** +**X**.

Конструктор действий **FlowSwitch \<T >** можно перетащить из **области элементов** в область Конструктор рабочих процессов в конструкторе действия **блок-схемы** . Используйте окно **Выбор типов** , которое отображает, чтобы указать тип (связанный в коде с <xref:System.Activities.Statements.FlowSwitch%601> по его универсальному параметру), полученный при вычислении <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Эта процедура создает действие <xref:System.Activities.Statements.FlowSwitch%601> с меткой **switch** в действии <xref:System.Activities.Statements.Flowchart>. @No__t_0 можно ввести в поле **выражение** окна **свойства** , щелкнув там, где текст подсказки — "введите выражение VB".

Наведите указатель мыши на конструктор действий **FlowSwitch \<T >** , чтобы привязать к квадратным маркерам, которые используются для связывания <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, появятся вокруг его границ. После перетаскивания конструктора действий **FlowSwitch < T \>** и других конструкторов действий в **блок-схеме**<xref:System.Activities.Activity> объекты, которые они представляют, можно связать друг с другом, чтобы указать порядок выполнения. Чтобы создать один из <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, связанных с <xref:System.Activities.Statements.FlowSwitch%601>, щелкните один из квадратных маркеров в периметре **FlowSwitch < t \>** и перетащите его (удерживая нажатой кнопку мыши) на один из маркеров, которые отображаются аналогичным образом вокруг целевое действие при наведении указателя мыши на свой конструктор. Отпустите кнопку мыши и стрелку из **FlowSwitch < T \>** откроется конструктор назначения, представляющий этот случай. Значение по умолчанию для этого варианта отображается на стрелке, и его можно изменить в поле " **вариант** " окна " **свойства** ".

### <a name="the-flowswitcht-properties"></a>Свойства \<T FlowSwitch >

В следующей таблице показаны свойства <xref:System.Activities.Statements.FlowSwitch%601> и описано их использование в конструкторе. Эти свойства можно изменить в сетке свойств или в области конструктора.

|Имя свойства|Обязательное значение|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Указывает выражение, вычисляемое для определения того, на какой из вариантов <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> следует переключиться в пути выполнения.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Задает уникальное сопоставление возможных результатов, полученных при вычислении <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, набору объектов <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Задает сопоставление, когда вычисление <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> не совпадает ни с одним значением, содержащимся в объекте <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>См. также

- [Блок-схема](../workflow-designer/flowchart-activity-designers.md)
- [Блок-схема](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)