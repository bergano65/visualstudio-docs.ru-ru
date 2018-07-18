---
title: Конструктор рабочих процессов - конструктора действий состояний
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 41abc73cce121ae4ebc247e20c0fcd2c60b8ec56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975863"
---
# <a name="state-activity-designer"></a>Конструктор State Activity

<xref:System.Activities.Statements.State> представляет состояние, в котором может находиться конечный автомат.

## <a name="using-the-state-activity-designer"></a>Использование конструктора действий состояний

Чтобы добавить <xref:System.Activities.Statements.State> рабочий процесс, перетащите **состояние** конструктора действий из **конечного автомата** раздел **элементов** и поместите его в <xref:System.Activities.Statements.StateMachine> действие в рабочей области конструктора рабочих процессов Windows. Действие <xref:System.Activities.Statements.State> можно перетащить в <xref:System.Activities.Statements.StateMachine> и переходы, добавленные позже. Переход также можно создать при помещении действия <xref:System.Activities.Statements.State> на поверхность. Чтобы добавить <xref:System.Activities.Statements.State> действия и создать переход за один шаг, перенесите **состояние** действия из **конечного автомата** раздел **элементов** и наведите его на другой состояние в конструкторе рабочих процессов. При наведении <xref:System.Activities.Statements.State> на другое <xref:System.Activities.Statements.State> вокруг другого <xref:System.Activities.Statements.State> будут отображены четыре треугольника. Если <xref:System.Activities.Statements.State> поместить на один из четырех треугольников, он будет добавлен к конечному автомату, а также будет добавлен переход состояния из исходного <xref:System.Activities.Statements.State> в размещенное целевое <xref:System.Activities.Statements.State>. Дополнительные сведения см. в разделе [перехода](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Свойства действия состояния в конструкторе рабочих процессов

В следующей таблице приведены свойства <xref:System.Activities.Statements.State>, которые можно задать с помощью конструктора рабочих процессов, и описано их использование в конструкторе. Некоторые из этих свойств можно изменить в таблице свойств, а некоторые из них ― в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.State> в заголовке. Значение по умолчанию — **состояние**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Statements.State.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Statements.State.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Указывает действие, которое выполняется при переходе в это состояние. При <xref:System.Activities.Statements.State> действия развернут, это значение может быть задано путем перетаскивания действия из **элементов** и помещения его в **входа** состояния.|
|<xref:System.Activities.Statements.State.Exit%2A>|False|Указывает действие, которое выполняется при переходе из этого состояния. Когда <xref:System.Activities.Statements.State> действия развернут, это значение может быть задано путем перетаскивания действия из **элементов** и помещения его в **выхода** состояния.|
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Перечисляет возможные переходы, исходящие из <xref:System.Activities.Statements.State>. Каждый элемент в списке имеет соединение со связанным <xref:System.Activities.Statements.Transition> и назначение <xref:System.Activities.Statements.State>. При щелчке по ссылке конструктор переключится в расширенное представление для <xref:System.Activities.Statements.Transition> или <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>См. также

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Конечное состояние](../workflow-designer/finalstate-activity-designer.md)
- [Переход](../workflow-designer/transition-activity-designer.md)