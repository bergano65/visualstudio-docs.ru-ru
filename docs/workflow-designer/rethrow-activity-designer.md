---
title: "Конструктор действия Rethrow | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Rethrow.UI"
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия Rethrow
Конструктор действия **Rethrow** служит для создания и настройки действия <xref:System.Activities.Statements.Rethrow>.  
  
## Действие Rethrow  
 Действие <xref:System.Activities.Statements.Rethrow> вызывает ранее вызванное исключение.Это действие может использоваться только в обработчике <xref:System.Activities.Statements.Catch> в действии <xref:System.Activities.Statements.TryCatch>.  
  
### Использование конструктора действия ReThrow  
 Конструктор действия **Rethrow** можно найти в категории **Обработка ошибокОбласти элементов**, открыв вкладку **Область элементов** в левой части [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(либо выберите пункт **Область элементов** в меню **Вид**, или нажмите CTRL\+ALT\+X\).  
  
 Конструктор действия **Rethrow** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] в любое место, где обычно размещаются действия, например, внутрь <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.Rethrow> со значением по умолчанию **DisplayName** для Throw.Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действия **Rethrow** либо в поле **DisplayName** таблицы свойств.  
  
### Свойства Rethrow  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Rethrow> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает дополнительное понятное имя действия <xref:System.Activities.Statements.ReThrow>.По умолчанию используется Rethrow.|  
  
## См. также  
 [Коллекция](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)