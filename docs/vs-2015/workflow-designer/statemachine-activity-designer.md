---
title: Конструктор действий StateMachine | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fc9d34e06ca443b39a1a57aa88fee1155f47a8c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660115"
---
# <a name="statemachine-activity-designer"></a>Конструктор действий StateMachine
Действие <xref:System.Activities.Statements.StateMachine> содержит коллекцию состояний и моделирует рабочие процессы с помощью известных принципов конечного автомата.

## <a name="using-the-statemachine-activity-designer"></a>Использование конструктора операций StateMachine
 Чтобы добавить действие <xref:System.Activities.Statements.StateMachine>, перетащите конструктор действий **StateMachine** из раздела **конечный автомат** на **панели элементов** и поместите его на поверхность [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Чтобы добавить дочернее состояние к этому <xref:System.Activities.Statements.StateMachine>у действию, перетащите <xref:System.Activities.Statements.State> или <xref:System.Activities.Core.Presentation.FinalState> из **панели элементов** и поместите его на **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Свойства действия StateMachine в конструкторе рабочих процессов
 В следующей таблице приведены свойства <xref:System.Activities.Statements.StateMachine>, которые можно задать с помощью конструктора рабочих процессов, и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них ― в области конструктора.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.StateMachine> в заголовке. Значение по умолчанию — **StateMachine**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Activity.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|

## <a name="see-also"></a>См. также раздел
 [Поток управления](../workflow-designer/control-flow-activity-designers.md) [блок-схемой](../workflow-designer/flowchart-activity-designer.md)