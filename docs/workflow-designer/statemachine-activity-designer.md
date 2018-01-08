---
title: "Конструктор действий StateMachine | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: "5"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 1800bfc9e60d52ea5c06bb94fdb765348a977681
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="statemachine-activity-designer"></a>Конструктор действий StateMachine
Действие <xref:System.Activities.Statements.StateMachine> содержит коллекцию состояний и моделирует рабочие процессы с помощью известных принципов конечного автомата.  
  
## <a name="using-the-statemachine-activity-designer"></a>Использование конструктора операций StateMachine  
 Чтобы добавить <xref:System.Activities.Statements.StateMachine> действие, перетащите **StateMachine** конструктора действий из **конечного автомата** раздел **элементов** и поместите его в [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] поверхность. Чтобы добавить состояние дочернего элемента к <xref:System.Activities.Statements.StateMachine> действие, перетащите <xref:System.Activities.Statements.State> или <xref:System.Activities.Core.Presentation.FinalState> из **элементов** и поместите его в **StateMachine**.  
  
### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Свойства действия StateMachine в конструкторе рабочих процессов  
 В следующей таблице приведены свойства <xref:System.Activities.Statements.StateMachine>, которые можно задать с помощью конструктора рабочих процессов, и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них ― в области конструктора.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.StateMachine> в заголовке. Значение по умолчанию — **StateMachine**. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций. <xref:System.Activities.Activity.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
  
## <a name="see-also"></a>См. также  
 [Блок-схемы](../workflow-designer/flowchart-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)