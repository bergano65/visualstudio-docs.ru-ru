---
title: Конструктор действий конструктор рабочих процессов-FlowSwitch &lt; T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6637682bd6ba649f27c1a53f3b1448629f03736
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711577"
---
# <a name="flowswitcht-activity-designer"></a>Конструктор действия FlowSwitch\<T>

Действие <xref:System.Activities.Statements.FlowSwitch%601> - это условный узел, который обеспечивает ветвление потока управления на основе критерия соответствия, когда требуется более двух альтернативных ветвей. Если ветвление потока требует наличие только двух ветвей, вместо этого следует использовать действие <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>Действие FlowSwitch \<T>

<xref:System.Activities.Statements.FlowSwitch%601>Действие содержит объект <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , возвращающий значение типа *T* (заданное универсальным параметром) при вычислении. Действие также содержит набор <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, который задает уникальное сопоставление на основе возможных результатов данного вычисления набору объектов <xref:System.Activities.Statements.FlowNode>. <xref:System.Activities.Statements.FlowNode>Выполненная — это объект, чье значение типа *T* соответствует значению вычисляемого объекта <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Вариант <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> может быть (дополнительно) предоставлен для варианта, в котором совпадений не было.

### <a name="using-the-flowswitcht-activity-designer"></a>Использование \<T> конструктора действий FlowSwitch

Конструктор **действий \<T> FlowSwitch** можно найти в категории блок- **схемы** **области элементов**, щелкнув вкладку **область элементов** в левой части конструктор рабочих процессов. Кроме того, можно выбрать **область элементов** в меню **вид** или нажать клавиши **CTRL** + **ALT** + **X**.

Конструктор **действий \<T> FlowSwitch** можно перетащить из **области элементов** в область Конструктор рабочих процессов в конструкторе действия **блок-схемы** . Используйте окно **Выбор типов** , в котором отображается, чтобы указать тип (связанный в коде с помощью <xref:System.Activities.Statements.FlowSwitch%601> его универсального параметра), полученный при вычислении <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Эта процедура создает <xref:System.Activities.Statements.FlowSwitch%601> действие с меткой **switch** в рамках <xref:System.Activities.Statements.Flowchart> действия. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Можно ввести в поле **выражение** окна **Свойства** , щелкнув там, где текст подсказки — «введите выражение VB».

Наведите указатель мыши на конструктор действий **FlowSwitch \<T> ** , чтобы <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> отобразить вокруг его границ квадратные маркеры, которые используются для связывания. После перетаскивания конструктора действий **FlowSwitch \><T** и других конструкторов действий в **блок-схеме**объекты, которые они представляют, можно связать друг с другом, <xref:System.Activities.Activity> чтобы указать порядок выполнения. Чтобы создать один из элементов <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> , связанных с <xref:System.Activities.Statements.FlowSwitch%601> , щелкните один из квадратных маркеров в периметре **FlowSwitch<T \> ** и перетащите его (удерживая нажатой кнопку мыши) на один из маркеров, которые отображаются аналогичным образом вокруг действия назначения при наведении указателя мыши на его конструктор. Отпустите кнопку мыши и стрелку из **FlowSwitch<T \> ** в конструкторе назначения, который представляет этот случай. Значение по умолчанию для этого варианта отображается на стрелке, и его можно изменить в поле " **вариант** " окна " **свойства** ".

### <a name="the-flowswitcht-properties"></a>Свойства FlowSwitch \<T>

В следующей таблице показаны свойства <xref:System.Activities.Statements.FlowSwitch%601> и описано их использование в конструкторе. Эти свойства можно изменить в сетке свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Верно|Указывает выражение, вычисляемое для определения того, на какой из вариантов <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> следует переключиться в пути выполнения.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Неверно|Задает уникальное сопоставление возможных результатов, полученных при вычислении <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, набору объектов <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Верно|Задает сопоставление, когда вычисление <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> не совпадает ни с одним значением, содержащимся в объекте <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>См. также статью

- [Блок-схема](../workflow-designer/flowchart-activity-designers.md)
- [Блок-схема](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
