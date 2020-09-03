---
title: '&lt; &gt; Конструктор действий FlowSwitch T | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27abb660766a7c04742eca221432af19f05f0d28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656643"
---
# <a name="flowswitchlttgt-activity-designer"></a>&lt; &gt; Конструктор активности FlowSwitch T
Действие <xref:System.Activities.Statements.FlowSwitch%601> - это условный узел, который обеспечивает ветвление потока управления на основе критерия соответствия, когда требуется более двух альтернативных ветвей. Если ветвление потока требует наличие только двух ветвей, вместо этого следует использовать действие <xref:System.Activities.Statements.FlowDecision>.

## <a name="the-flowswitcht-activity"></a>Действие FlowSwitch \<T>
 <xref:System.Activities.Statements.FlowSwitch%601>Действие содержит объект <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , возвращающий значение типа *T* (заданное универсальным параметром) при вычислении. Действие также содержит набор <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, который задает уникальное сопоставление на основе возможных результатов данного вычисления набору объектов <xref:System.Activities.Statements.FlowNode>. <xref:System.Activities.Statements.FlowNode>Выполненная — это объект, чье значение типа *T* соответствует значению вычисляемого объекта <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Вариант <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> может быть (дополнительно) предоставлен для варианта, в котором совпадений не было.

### <a name="using-the-flowswitcht-activity-designer"></a>Использование \<T> конструктора действий FlowSwitch
 Конструктор **действий \<T> FlowSwitch** можно найти в категории блок- **схемы** **области элементов**, щелкнув вкладку **область элементов** в левой части окна [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать пункт **панель инструментов** в меню **вид** или CTRL + ALT + X).

 Конструктор **действий \<T> FlowSwitch** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область в конструкторе действия **блок-схемы** . Используйте окно **Выбор типов** , в котором отображается, чтобы указать тип (связанный в коде с помощью <xref:System.Activities.Statements.FlowSwitch%601> его универсального параметра), полученный при вычислении <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Эта процедура создает <xref:System.Activities.Statements.FlowSwitch%601> действие с меткой **switch** в рамках <xref:System.Activities.Statements.Flowchart> действия. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Можно ввести в поле **выражение** окна **Свойства** , щелкнув там, где текст подсказки — «введите выражение VB».

 Наведите указатель мыши на конструктор действий **FlowSwitch \<T> ** , чтобы <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> отобразить вокруг его границ квадратные маркеры, которые используются для связывания. После перетаскивания конструктора действий **FlowSwitch \><T** и других конструкторов действий в **блок-схеме**объекты, которые они представляют, можно связать друг с другом, <xref:System.Activities.Activity> чтобы указать порядок выполнения. Чтобы создать один из элементов <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> , связанных с <xref:System.Activities.Statements.FlowSwitch%601> , щелкните один из квадратных маркеров в периметре **FlowSwitch \<T> ** и перетащите его (удерживая нажатой кнопку мыши) на один из маркеров, похожих на действие назначения, когда указатель мыши помещается над его конструктором. Отпустите кнопку мыши и стрелку из **FlowSwitch \<T> ** в конструкторе назначения, который представляет этот случай. Значение по умолчанию для этого варианта отображается на стрелке, и его можно изменить в поле " **вариант** " окна " **свойства** ".

### <a name="the-flowswitcht-properties"></a>Свойства FlowSwitch \<T>
 В следующей таблице показаны свойства <xref:System.Activities.Statements.FlowSwitch%601> и описано их использование в конструкторе. Эти свойства можно изменить в сетке свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Верно|Указывает выражение, вычисляемое для определения того, на какой из вариантов <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> следует переключиться в пути выполнения.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Неверно|Задает уникальное сопоставление возможных результатов, полученных при вычислении <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, набору объектов <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Верно|Задает сопоставление, когда вычисление <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> не совпадает ни с одним значением, содержащимся в объекте <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>См. также:
 Блок [-схема](../workflow-designer/flowchart-activity-designers.md) [Flowchart](../workflow-designer/flowchart-activity-designer.md) [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)