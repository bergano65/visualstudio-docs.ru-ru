---
title: Конструктор действий Assign | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: c27d70f7dbff9d7f9d30d7dda34c5c2c98bfe891
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281272"
---
# <a name="assign-activity-designer"></a>Конструктор действий Assign
**Назначить** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Assign> действия.  
  
## <a name="the-assign-activity"></a>Действие Assign  
 Действие <xref:System.Activities.Statements.Assign> присваивает значение переменной или аргументу.  
  
### <a name="using-the-assign-activity-designer"></a>Использование конструктора действия Assign  
 **Назначить** конструктора действий можно найти в **примитивы** категории **элементов**, который нажав **элементов**вкладка (Кроме того, выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **Назначить** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности где когда-либо обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Assign> действие по умолчанию **DisplayName** из назначения. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **назначить** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
### <a name="the-assign-properties"></a>Свойства Assign  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Assign> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Assign>. Значение по умолчанию - Assign. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|Переменная или аргумент, которым присваивается <xref:System.Activities.Statements.Assign.Value%2A>. Должно быть допустимым идентификатором Visual Basic. Чтобы задать свойство, введите выражение Visual Basic в **для** поле **назначить** действие конструктора или в сетке свойств.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|Да|Значение, присваиваемое переменной. Чтобы задать <xref:System.Activities.Statements.Assign.Value%2A>, введите выражение Visual Basic в **значение** поле **назначить** действие конструктора или в сетке свойств.|  
  
## <a name="see-also"></a>См. также  
 [Примитивы](../workflow-designer/primitives-activity-designers.md)   
 [Задержка](../workflow-designer/delay-activity-designer.md)   
 [Метод InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)