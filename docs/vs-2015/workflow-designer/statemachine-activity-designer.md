---
title: Конструктор действия StateMachine | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 1f768142ce3cf71b254e6740a87895f5626372fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559149"
---
# <a name="statemachine-activity-designer"></a>Конструктор действий StateMachine
Действие <xref:System.Activities.Statements.StateMachine> содержит коллекцию состояний и моделирует рабочие процессы с помощью известных принципов конечного автомата.  
  
## <a name="using-the-statemachine-activity-designer"></a>Использование конструктора операций StateMachine  
 Чтобы добавить <xref:System.Activities.Statements.StateMachine> действие, перетащите **StateMachine** конструктор из **конечный автомат** раздел **элементов** и сбросьте его в [!INCLUDE[wfd1](../includes/wfd1-md.md)] Рабочая область. Чтобы добавить состояние дочернего элемента к <xref:System.Activities.Statements.StateMachine> действие, перетащите <xref:System.Activities.Statements.State> или <xref:System.Activities.Core.Presentation.FinalState> из **элементов** и сбросьте его в **StateMachine**.  
  
### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Свойства действия StateMachine в конструкторе рабочих процессов  
 В следующей таблице приведены свойства <xref:System.Activities.Statements.StateMachine>, которые можно задать с помощью конструктора рабочих процессов, и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них ― в области конструктора.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.StateMachine> в заголовке. Значение по умолчанию — **StateMachine**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Activity.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
  
## <a name="see-also"></a>См. также  
 [Блок-схема](../workflow-designer/flowchart-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)