---
title: "Конструктор действий Assign | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Assign.UI"
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Конструктор действий Assign
Конструктор действия **Assign** служит для создания и настройки действия <xref:System.Activities.Statements.Assign>.  
  
## Действие Assign  
 Действие <xref:System.Activities.Statements.Assign> присваивает значение переменной или аргументу.  
  
### Использование конструктора действия Assign  
 Конструктор действия **Assign** можно найти в категории **Примитивы** в **Области элементов**, открыв вкладку **Область элементов** \(либо выберите **Область элементов** в меню **Вид** или нажмите CTRL\+ALT\+X\).  
  
 Конструктор действия **Assign** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], где обычно размещаются действия, например внутрь <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.Assign>, где значение **DisplayName** по умолчанию равно Assign.<xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действия **Assign** либо в поле **DisplayName** таблицы свойств.  
  
### Свойства Assign  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Assign> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Понятное имя действия <xref:System.Activities.Statements.Assign>.Значение по умолчанию — Assign.Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.Assign.To%2A>|Да|Переменная или аргумент, которым присваивается <xref:System.Activities.Statements.Assign.Value%2A>.Должно быть допустимым идентификатором Visual Basic.Чтобы установить это свойство, введите выражение Visual Basic в поле **To** конструктора действия **Assign** или в таблицу свойств.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|Да|Значение, присваиваемое переменной.Чтобы установить <xref:System.Activities.Statements.Assign.Value%2A>, введите выражение Visual Basic в поле **Value** конструктора действия **Assign** или в таблицу свойств.|  
  
## См. также  
 [Базовые функции](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)