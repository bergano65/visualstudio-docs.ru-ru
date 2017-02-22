---
title: "InvokeDelegate | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InvokeDelegate Designer"
  - "System.Activities.Statements.InvokeDelegate.UI"
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "sdanie"
manager: "erikre"
---
# InvokeDelegate
Конструктор **InvokeDelegate** используется для создания и настройки действия <xref:System.Activities.Statements.InvokeDelegate>.  
  
## Действие InvokeDelegate  
 <xref:System.Activities.Statements.InvokeDelegate> вызывает открытый делегат.  
  
### Использование конструктора действий InvokeDelegate  
 Конструктор операций **InvokeDelegate** можно найти в категории **ПримитивыОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Панель инструментов** из меню **Просмотр** или же CTRL\+ALT\+X.\)  
  
 Конструктор операций **InvokeDelegate** можно перетащить из **Области элементов** в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] в любое место, куда обычно размещаются действия, например, внутри <xref:System.Activities.Statements.Sequence>.Это создает действие <xref:System.Activities.Statements.InvokeDelegate> с именем по умолчанию <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate.<xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **InvokeDelegate** либо в поле **DisplayName** сетки свойств.  
  
### Свойства InvokeDelegate  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.InvokeDelegate> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств и некоторые свойства ― в области конструктора [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Понятное имя действия <xref:System.Activities.Statements.InvokeDelegate>.Значение по умолчанию: InvokeDelegate.<br /><br /> Несмотря на то, что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Имя метода <xref:System.Activities.Statements.ActivityDelegate>, вызываемого, когда выполняется действие.Это свойство можно изменить в области конструктора.Это свойство обязательное.|  
|<xref:System.Activities.Statements.InvokeMethod.DelegateArguments%2A>|False|Коллекция аргументов вызванного делегата.Ключи — это имена объектов <xref:System.Activities.Statements.ActivityDelegateParameter> в объекте <xref:System.Activities.Statements.ActivityDelegate> и значения, которые являются аргументами тех выражений, которые вычисляются и присваиваются соответствующим объектам <xref:System.Activities.Statements.ActivityDelegateParameter>.В сетке свойств нажмите кнопку с многоточием в поле **Аргументы делегата**, после чего отобразится диалоговое окно **Аргументы делегата**, в котором можно установить это свойство.Щелкните поле **Создать аргумент**, чтобы добавить аргументы.|  
  
## См. также  
 [Как определить и использовать делегатов действий в конструкторе рабочих процессов](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)