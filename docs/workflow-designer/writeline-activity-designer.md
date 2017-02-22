---
title: "Конструктор действия WriteLine | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.WriteLine.UI"
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия WriteLine
Конструктор операций **WriteLine** используется для создания и настройки действия <xref:System.Activities.Statements.WriteLine>.  
  
## Операция WriteLine  
 Операция <xref:System.Activities.Statements.Writeline> выполняет запись текста в указанный объект <xref:System.IO.TextWriter>.Если не указано <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.Writeline> выполняет запись текста к консоли.  
  
### Использование конструктора действий WriteLine  
 Конструктор операций **WriteLine** можно найти в категории **ПримитивыОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или же CTRL\+ALT\+X.\)  
  
 Конструктор операций **WriteLine** можно перетащить из **Области элементов** в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] в любое место, куда обычно размещаются действия, например, внутри <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.WriteLine> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для WriteLine.<xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **WriteLine** либо в поле **DisplayName** таблицы свойств.  
  
### Свойства WriteLine  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.WriteLine> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств, а некоторые из них ― в области конструктора [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Понятное имя действия <xref:System.Activities.Statements.WriteLine>.Значение по умолчанию WriteLine.Для значения <xref:System.Activities.Activity.DisplayName%2A> нет жестких требований, однако лучше всего всегда использовать такое значение.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Текст для записи.Для установки свойства введите выражение Visual Basic в поле **Text** конструктора операций **WhiteLine** или в таблицу свойств.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Нет|Класс <xref:System.IO.TextWriter>, в который <xref:System.Activities.Statements.WriteLine> записывает <xref:System.Activities.Statements.WriteLine.Text%2A>.По умолчанию — консоль.|  
  
## См. также  
 [Базовые функции](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)