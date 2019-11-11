---
title: Конструктор действий FinalState | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dff9793becc3e0619d42b642609273f328c6aa73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656726"
---
# <a name="finalstate-activity-designer"></a>Конструктор FinalState Activity
Конструктор <xref:System.Activities.Core.Presentation.FinalState> используется для создания <xref:System.Activities.Statements.State>, которое завершает экземпляр конечного автомата.

## <a name="using-the-finalstate-activity-designer"></a>Использование конструктора действий FinalState
 Конструктор **FinalState** используется для создания <xref:System.Activities.Statements.State>, предварительно настроенного в качестве завершающего состояния конечного автомата. Для <xref:System.Activities.Statements.State>, созданного с помощью конструктора действий <xref:System.Activities.Core.Presentation.FinalState>, свойство <xref:System.Activities.Statements.State.IsFinal%2A> имеет значение **true**, не имеет <xref:System.Activities.Statements.State.Exit%2A> действий и не исходит от него переходов. Чтобы использовать конструктор действий <xref:System.Activities.Core.Presentation.FinalState> для добавления действия <xref:System.Activities.Statements.State>, которое предварительно настроено в качестве завершающего состояния на конечный автомат, перетащите конструктор действий **FinalState** из раздела **конечный автомат** области **элементов** и поместите его на страницу Конструктор рабочих процессов. Конструктор действий <xref:System.Activities.Core.Presentation.FinalState> можно перетащить в <xref:System.Activities.Statements.StateMachine> и переходы, добавленные позже. Переход также можно создать при помещении конструктора действий <xref:System.Activities.Core.Presentation.FinalState> на поверхность. Дополнительные сведения о создании переходов см. в разделе [Переход](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Свойства действия состояния в конструкторе рабочих процессов
 В следующей таблице приведены свойства, которые можно задать с помощью конструктора <xref:System.Activities.Core.Presentation.FinalState>, и описано их использование в конструкторе. Некоторые из этих свойств можно изменить в таблице свойств, а некоторые из них ― в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.State> в заголовке. Значение по умолчанию — **State**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Statements.State.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Statements.State.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Указывает действие, которое выполняется при переходе в это состояние. Это значение можно задать, перетащив действие с **панели элементов** на <xref:System.Activities.Statements.State.Entry%2A> раздел состояния.|

## <a name="see-also"></a>См. также
 [Переход](../workflow-designer/transition-activity-designer.md) [состояния](../workflow-designer/state-activity-designer.md) [StateMachine](../workflow-designer/statemachine-activity-designer.md)