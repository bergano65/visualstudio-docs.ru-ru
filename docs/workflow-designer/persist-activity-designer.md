---
title: "Конструктор действия Persist | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Persist.UI"
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Конструктор действия Persist
Конструктор действия **Persist** служит для создания и настройки действия <xref:System.Activities.Statements.Persist>.  
  
## Действие Persist  
 Действие <xref:System.Activities.Statements.Persist> сохраняет рабочий процесс на диск, если это возможно.Действие <xref:System.Activities.Statements.Persist> не может быть выполнено в зоне несохраняемости, например в пределах действия <xref:System.Activities.Statements.TransactionScope>.Если действие <xref:System.Activities.Statements.Persist> все же используется в области несохраняемости, то во время выполнения возникнет исключение.  
  
### Использование конструктора действия Persist  
 Конструктор действия **Persist** можно найти в категории **ВыполнениеОбласти элементов**, открыв вкладку **Область элементов** \(либо выберите **Область элементов** в меню **Вид** или нажмите CTRL\+ALT\+X\).  
  
 Конструктор действия **Persist** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], где обычно размещаются действия, например внутрь <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.Persist>, где значение **DisplayName** по умолчанию равно Persist.<xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действия **Persist** либо в поле **DisplayName** таблицы свойств.  
  
### Свойства Persist  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Persist> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Persist>.По умолчанию используется значение Persist.Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|  
  
## См. также  
 [Среда выполнения](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)