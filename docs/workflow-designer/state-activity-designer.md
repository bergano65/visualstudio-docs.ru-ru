---
title: Конструктор действий конструктор рабочих процессов состояния
description: Сведения о действии StateMachine и о том, как можно использовать конструктор действий состояния для добавления состояния в рабочий процесс.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: d5dbe0a14b007ad8e916aa9b2d8d765402dbe66b
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433990"
---
# <a name="state-activity-designer"></a>Конструктор State Activity

<xref:System.Activities.Statements.State> представляет состояние, в котором может находиться конечный автомат.

## <a name="using-the-state-activity-designer"></a>Использование конструктора действий состояний

Чтобы добавить в <xref:System.Activities.Statements.State> Рабочий процесс, перетащите конструктор активности **состояний** из раздела **конечный автомат** **области элементов** и поместите его в <xref:System.Activities.Statements.StateMachine> действие на конструктор рабочих процессовной поверхности. Действие <xref:System.Activities.Statements.State> можно сбросить в <xref:System.Activities.Statements.StateMachine> и переходы, добавленные позже. Переход также можно создать при помещении действия <xref:System.Activities.Statements.State> на поверхность. Чтобы добавить <xref:System.Activities.Statements.State> действие и создать переход за один шаг, перетащите действие **State** из раздела **конечный автомат** **области элементов** и наведите его на другое состояние в конструкторе рабочих процессов. При наведении <xref:System.Activities.Statements.State> на другое <xref:System.Activities.Statements.State> вокруг другого <xref:System.Activities.Statements.State> будут отображены четыре треугольника. Если объект <xref:System.Activities.Statements.State> бросить в один из четырех треугольников, он будет добавлен к конечному автомату, а также будет добавлен переход состояния из исходного <xref:System.Activities.Statements.State> в сброшенное целевое <xref:System.Activities.Statements.State>. Дополнительные сведения см. в разделе [Переход](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Свойства действия состояния в конструкторе рабочих процессов

В следующей таблице приведены свойства <xref:System.Activities.Statements.State>, которые можно задать с помощью конструктора рабочих процессов, и описано их использование в конструкторе. Некоторые из этих свойств можно изменить в таблице свойств, а некоторые из них ― в области конструктора.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Неверно|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.State> в заголовке. Значение по умолчанию — **State**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Statements.State.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Statements.State.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.State.Entry%2A>|Неверно|Указывает действие, которое выполняется при переходе в это состояние. При <xref:System.Activities.Statements.State> развертывании действия это значение можно задать, перетащив действие из **панели элементов** в раздел **записи** состояния.|
|<xref:System.Activities.Statements.State.Exit%2A>|Неверно|Указывает действие, которое выполняется при переходе из этого состояния. Если <xref:System.Activities.Statements.State> действие развернуто, это значение можно задать, перетащив действие из **панели элементов** и выполнив его в раздел **Exit** состояния.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Неверно|Перечисляет возможные переходы, исходящие из <xref:System.Activities.Statements.State>. Каждый элемент в списке имеет соединение со связанным <xref:System.Activities.Statements.Transition> и назначение <xref:System.Activities.Statements.State>. При щелчке по ссылке конструктор переключится в расширенное представление для <xref:System.Activities.Statements.Transition> или <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>См. также раздел

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Переход](../workflow-designer/transition-activity-designer.md)
