---
title: Конструктор рабочих процессов - конструктор действий StateMachine
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 52cbd0e27934d5d13c0e83c6c8e3e87281aa1b5a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972905"
---
# <a name="statemachine-activity-designer"></a>Конструктор действий StateMachine

Действие <xref:System.Activities.Statements.StateMachine> содержит коллекцию состояний и моделирует рабочие процессы с помощью известных принципов конечного автомата.

## <a name="using-the-statemachine-activity-designer"></a>Использование конструктора операций StateMachine

Чтобы добавить <xref:System.Activities.Statements.StateMachine> действие, перетащите **StateMachine** конструктор из **конечный автомат** раздел **элементов** и поместите его в конструкторе рабочих процессов Рабочая область. Чтобы добавить состояние дочернего элемента к <xref:System.Activities.Statements.StateMachine> действие, перетащите <xref:System.Activities.Statements.State> или <xref:System.Activities.Core.Presentation.FinalState> из **элементов** и сбросьте его в **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Свойства действия StateMachine в конструкторе рабочих процессов

В следующей таблице приведены свойства <xref:System.Activities.Statements.StateMachine>, которые можно задать с помощью конструктора рабочих процессов, и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них ― в области конструктора.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.StateMachine> в заголовке. Значение по умолчанию — **StateMachine**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Activity.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|

## <a name="see-also"></a>См. также

- [Блок-схема](../workflow-designer/flowchart-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)