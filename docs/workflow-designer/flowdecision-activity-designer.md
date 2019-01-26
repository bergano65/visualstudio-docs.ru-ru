---
title: Конструктор рабочих процессов - конструктор действия FlowDecision
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3320192e75d47194f7421f49ab28925306540ce4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998681"
---
# <a name="flowdecision-activity-designer"></a>Конструктор действия FlowDecision

Узел <xref:System.Activities.Statements.FlowDecision> - это специализированный узел, который обеспечивает ветвление для передачи управления одной из двух альтернатив в зависимости от указанного условия. Если ветвление требует наличие более двух ветвей, следует вместо этого метода использовать <xref:System.Activities.Statements.FlowSwitch%601>.

## <a name="the-flowdecision-node"></a>Узел The FlowDecision

Используйте <xref:System.Activities.Statements.FlowDecision>, когда поток можно разветвить на два пути. Узел <xref:System.Activities.Statements.FlowDecision> обладает <xref:System.Activities.Statements.FlowDecision.Condition%2A> и <xref:System.Activities.Statements.FlowNode>, связанными с двумя возможными значениями: <xref:System.Activities.Statements.FlowDecision.True%2A> или <xref:System.Activities.Statements.FlowDecision.False%2A>. Выполняется оценка <xref:System.Activities.Statements.FlowDecision.Condition%2A>, причем значение этой оценки определяет следующее <xref:System.Activities.Statements.FlowNode>, которое будет обработано внутри <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Использование конструктора FlowDecision

**FlowDecision** конструктора можно найти в **блок-схема** категории **элементов**, который нажав **элементов** Вкладка конструктором рабочих процессов. Можно также выбрать **элементов** из **представление** меню или нажмите клавишу **Ctrl**+**Alt** + **X**.

**FlowDecision** конструктора можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов в **блок-схема** конструктора действий. При этом создается <xref:System.Activities.Statements.FlowDecision> с меткой **решение** в <xref:System.Activities.Statements.Flowchart> действия. Мышь над конструктором и **True** и **False** появятся квадратные маркеры для обеих ветвей.

После перетаскивания **FlowDecision** конструктора и других конструкторов в **блок-схема**, узлы могут быть связаны друг с другом, чтобы указать порядок выполнения. Чтобы создать связь между исходным узлом (включая **True** и **False** ветвей **FlowDecision**) и узел назначения, мышь над конструктором исходного узла и на каждой его стороне появятся квадратные маркеры. Щелкните один из них и перетащите его, удерживая кнопку мыши, к одному из маркеров, которые похожим образом появляются на целевом узле при наведении мыши. Отпустите кнопку мыши для создания ссылки между этими двумя узлами, что отмечено стрелкой от исходного к целевому конструктору.

Выражение, указывающее, <xref:System.Activities.Statements.FlowDecision.Condition%2A> можно ввести в **условие** поле **свойства** окно, нажав кнопку, где написано «Введите выражение VB».

### <a name="the-flowdecision-properties"></a>Свойства FlowDecision

В следующей таблице показаны свойства <xref:System.Activities.Statements.FlowDecision> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Условие, которое определяет, какой из путей будет использован потоком данных.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Путь, предпринятый при удовлетворении условия <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Путь, предпринятый при неудовлетворении условия <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|

## <a name="see-also"></a>См. также

- [Блок-схема](../workflow-designer/flowchart-activity-designers.md)
- [Блок-схема](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)