---
title: "Конструктор действия Delay | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Delay.UI"
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Конструктор действия Delay
Конструктор действия **Delay** служит для создания и настройки действия <xref:System.Activities.Statements.Delay>.  
  
## Действие Delay  
 Действие <xref:System.Activities.Statements.Delay> откладывает выполнение рабочего процесса на указанное время.  
  
### Использование конструктора действия Delay  
 Конструктор действия **Delay** можно найти в категории **ПримитивыОбласти элементов**, открыв вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(либо выберите **Область элементов** в меню **Вид** или нажмите CTRL\+ALT\+X\).  
  
 Конструктор действия **Delay** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], где обычно размещаются действия, например внутрь <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.Delay>, где значение <xref:System.Activities.Activity.DisplayName%2A> по умолчанию равно Delay.<xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действия **Delay** либо в поле **DisplayName** таблицы свойств.  
  
### Свойства Delay  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Delay> и описано их использование в конструкторе.Эти свойства можно изменить в сетке свойств, а некоторые ― в области конструктора [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|------------------|-----------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Delay>.Значение по умолчанию — Delay.Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Период времени, на который задерживается выполнение рабочего процесса.Это свойство задается в таблице свойств.Введите литерал <xref:System.TimeSpan> в формате 00:00:00 или выражение Visual Basic для указания периода времени.|  
  
## См. также  
 [Базовые функции](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay Activity Designer](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)