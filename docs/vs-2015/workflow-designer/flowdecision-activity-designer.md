---
title: Конструктор действий FlowDecision | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b93d88462d5e3984b06c671455439e9bd2b07c5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656691"
---
# <a name="flowdecision-activity-designer"></a>Конструктор действия FlowDecision
<xref:System.Activities.Statements.FlowDecision> — это специализированный узел, который обеспечивает ветвление для передачи управления одной из двух альтернатив в зависимости от указанного условия. Если поток требует наличие более двух ветвей, следует вместо этого метода использовать <xref:System.Activities.Statements.FlowSwitch%601>.

## <a name="the-flowdecision-node"></a>Узел The FlowDecision
 Используйте <xref:System.Activities.Statements.FlowDecision>, когда поток можно разветвить на два пути. Узел <xref:System.Activities.Statements.FlowDecision> обладает <xref:System.Activities.Statements.FlowDecision.Condition%2A> и <xref:System.Activities.Statements.FlowNode>, связанными с двумя возможными значениями: <xref:System.Activities.Statements.FlowDecision.True%2A> или <xref:System.Activities.Statements.FlowDecision.False%2A>. Выполняется оценка <xref:System.Activities.Statements.FlowDecision.Condition%2A>, причем значение этой оценки определяет следующее <xref:System.Activities.Statements.FlowNode>, которое будет обработано внутри <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Использование конструктора FlowDecision
 Конструктор **FlowDecision** можно найти в категории блок- **схемы** **области элементов**, щелкнув вкладку **область элементов** на [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать **панель инструментов** в меню **вид** или CTRL + ALT + X)

 Конструктор **FlowDecision** можно перетащить из **панели элементов** в область [!INCLUDE[wfd2](../includes/wfd2-md.md)] в конструкторе действия **блок-схемы** . При этом создается <xref:System.Activities.Statements.FlowDecision> с меткой **принятия решений** в рамках действия <xref:System.Activities.Statements.Flowchart>. Наведите указатель мыши на конструктор и появятся квадратные дескрипторы **true** и **false** для двух ветвей.

 После перетаскивания конструктора **FlowDecision** и других конструкторов на **блок-схему**узлы можно связать друг с другом, чтобы указать порядок выполнения. Чтобы создать связь между исходным узлом (в том числе ветвями **true** и **false** **FlowDecision**) и узлом назначения, наведите указатель мыши на конструктор исходного узла и квадратный маркер появится на каждой стороне. Щелкните один из них и перетащите его, удерживая кнопку мыши, к одному из маркеров, которые похожим образом появляются на целевом узле при наведении мыши. Отпустите кнопку мыши для создания ссылки между этими двумя узлами, что отмечено стрелкой от исходного к целевому конструктору.

 Выражение, указывающее, что <xref:System.Activities.Statements.FlowDecision.Condition%2A> можно ввести в поле **условие** окна **свойства** , щелкнув там, где текст подсказки — «введите выражение VB».

### <a name="the-flowdecision-properties"></a>Свойства FlowDecision
 В следующей таблице показаны свойства <xref:System.Activities.Statements.FlowDecision> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Условие, которое определяет, какой из путей будет использован потоком данных.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Путь потока управления при удовлетворении условия <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Путь потока управления при неудовлетворении условия <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|

## <a name="see-also"></a>См. также раздел
 [Блок-](../workflow-designer/flowchart-activity-designers.md) [схема блок-](../workflow-designer/flowchart-activity-designer.md) схемы [FlowSwitch \<T >](../workflow-designer/flowswitch-t-activity-designer.md)