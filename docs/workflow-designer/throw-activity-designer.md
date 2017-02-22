---
title: "Конструктор действия Throw | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Throw.UI"
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия Throw
Конструктор операций  **Throw** используется для создания и настройки действия <xref:System.Activities.Statements.Throw>.  
  
## Действие Throw  
 Действие <xref:System.Activities.Statements.Throw> вызывает исключение.  
  
### Использование конструктора операций Throw  
 Конструктор операций  **Throw** можно найти в категории **Обработка ошибокОбласти элементов**, нажав на вкладку **Область элементов** по левую сторону [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или нажмите CTRL\+ALT\+X\).  
  
 Конструктор операций  **Throw** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], куда обычно размещаются действия, например, внутри <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.Throw> со значением по умолчанию **DisplayName** для Throw.Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций  **Throw** либо в поле **DisplayName** таблицы свойств.Свойство <xref:System.Activities.Statements.Throw.Exception%2A> должно редактироваться в таблице свойств.  
  
### Свойства Throw  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Throw> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает дополнительное понятное имя действия <xref:System.Activities.Statements.Throw>.По умолчанию используется Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|Да|Вызываемое исключение.Данное исключение должно быть производным от класса <xref:System.Exception>.Чтобы указать исключение, введите выражение Visual Basic в таблице свойств.|  
  
## См. также  
 [Коллекция](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw Activity Designer](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)