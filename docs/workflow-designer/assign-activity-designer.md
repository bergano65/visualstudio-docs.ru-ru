---
title: "Конструктор действий Assign | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: bb816aee41f86e2cbdc71e93b78f1a9e09249a00
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="assign-activity-designer"></a>Конструктор действий Assign
**Назначить** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Assign> действия.  
  
## <a name="the-assign-activity"></a>Действие Assign  
 Действие <xref:System.Activities.Statements.Assign> присваивает значение переменной или аргументу.  
  
### <a name="using-the-assign-activity-designer"></a>Использование конструктора действия Assign  
 **Назначить** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **элементов**вкладка (либо выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Назначить** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности где-либо обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Assign> действия по умолчанию **DisplayName** равно Assign. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **назначить** конструктора или в **DisplayName** поле сетки свойств.  
  
### <a name="the-assign-properties"></a>Свойства Assign  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Assign> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Assign>. Значение по умолчанию - Assign. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|Переменная или аргумент, которым присваивается <xref:System.Activities.Statements.Assign.Value%2A>. Должно быть допустимым идентификатором Visual Basic. Чтобы задать свойство, введите выражение Visual Basic в **для** поле на **назначить** действие конструктора или в сетке свойств.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|Да|Значение, присваиваемое переменной. Чтобы задать <xref:System.Activities.Statements.Assign.Value%2A>, введите выражение Visual Basic в **значение** поле на **назначить** действие конструктора или в сетке свойств.|  
  
## <a name="see-also"></a>См. также  
 [Примитивы](../workflow-designer/primitives-activity-designers.md)   
 [Задержка](../workflow-designer/delay-activity-designer.md)   
 [Метод InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)