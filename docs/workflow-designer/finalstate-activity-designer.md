---
title: Конструктор действий конструктор рабочих процессов FinalState
description: Узнайте, как можно использовать конструктор FinalState для создания состояния, завершающего экземпляр конечного автомата.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a6ec51d17453a13f8c3ab1adffc5447afb5db7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894183"
---
# <a name="finalstate-activity-designer"></a>Конструктор FinalState Activity

Конструктор <xref:System.Activities.Core.Presentation.FinalState> используется для создания <xref:System.Activities.Statements.State>, которое завершает экземпляр конечного автомата.

## <a name="using-the-finalstate-activity-designer"></a>Использование конструктора действий FinalState

Конструктор **FinalState** используется для создания <xref:System.Activities.Statements.State> , который предварительно настроен в качестве завершающего состояния конечного автомата. Для <xref:System.Activities.Statements.State> свойства, созданного с помощью <xref:System.Activities.Core.Presentation.FinalState> конструктора действий <xref:System.Activities.Statements.State.IsFinal%2A> , свойство имеет значение **true**, не имеет <xref:System.Activities.Statements.State.Exit%2A> действия и не исходит от него переходов. Чтобы использовать <xref:System.Activities.Core.Presentation.FinalState> конструктор действий для добавления <xref:System.Activities.Statements.State> действия, которое предварительно настроено в качестве завершающего состояния на конечный автомат, перетащите конструктор действий **FinalState** из раздела **конечный автомат** на **панели элементов** и поместите его в конструктор рабочих процессов. Конструктор действий <xref:System.Activities.Core.Presentation.FinalState> можно перетащить в <xref:System.Activities.Statements.StateMachine> и переходы, добавленные позже. Переход также можно создать при помещении конструктора действий <xref:System.Activities.Core.Presentation.FinalState> на поверхность. Дополнительные сведения о создании переходов см. в разделе [Переход](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Свойства действия состояния в конструкторе рабочих процессов

В следующей таблице приведены свойства, которые можно задать с помощью конструктора <xref:System.Activities.Core.Presentation.FinalState>, и описано их использование в конструкторе. Некоторые из этих свойств можно изменить в таблице свойств, а некоторые из них ― в области конструктора.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.State> в заголовке. Значение по умолчанию — **State**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Statements.State.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Statements.State.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Указывает действие, которое выполняется при переходе в это состояние. Это значение можно задать, перетащив действие из **панели элементов** в <xref:System.Activities.Statements.State.Entry%2A> раздел состояния.|

## <a name="see-also"></a>См. также раздел

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Состояние](../workflow-designer/state-activity-designer.md)
- [Переход](../workflow-designer/transition-activity-designer.md)