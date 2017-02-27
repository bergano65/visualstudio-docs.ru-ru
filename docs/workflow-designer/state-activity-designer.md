---
title: "Конструктор State Activity | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.State.UI"
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 5
---
# Конструктор State Activity
<xref:System.Activities.Statements.State> представляет состояние, в котором может находиться конечный автомат.  
  
## Использование конструктора действий состояний  
 Чтобы добавить <xref:System.Activities.Statements.State> в рабочий процесс, перетащите конструктор действий **Состояние** из раздела **Конечный автоматобласти элементов** и поместите его в действие <xref:System.Activities.Statements.StateMachine> в области [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Действие <xref:System.Activities.Statements.State> можно перетащить в <xref:System.Activities.Statements.StateMachine> и переходы добавленные позже. Переход также можно создать при помещении действия <xref:System.Activities.Statements.State> на поверхность.Чтобы добавить действие <xref:System.Activities.Statements.State> и создать переход за один шаг, перетащите действие **Состояние** из раздела **Конечный автоматобласти элементов** и наведите его на другое состояние в конструкторе рабочих процессов.При наведении <xref:System.Activities.Statements.State> на другое <xref:System.Activities.Statements.State> вокруг другого <xref:System.Activities.Statements.State> будут отображены четыре треугольника.Если <xref:System.Activities.Statements.State> поместить на один из четырех треугольников, он будет добавлен к конечному автомату, а также будет добавлен переход состояния из исходного <xref:System.Activities.Statements.State> в размещенное целевое <xref:System.Activities.Statements.State>.Дополнительные сведения см. в разделе [Переход](../workflow-designer/transition-activity-designer.md).  
  
### Свойства действия состояния в конструкторе рабочих процессов  
 В следующей таблице приведены свойства <xref:System.Activities.Statements.State>, которые можно настроить с помощью конструктора рабочих процессов, и описано их использование в конструкторе.Некоторые из этих свойств можно изменить в сетке свойств, а некоторые ― в области конструктора.  
  
|Имя свойства|Обязательно|Использование|  
|------------------|-----------------|-------------------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.State> в заголовке.Значение по умолчанию: **Состояние**.Значение можно дополнительно изменить в сетке свойств или напрямую в заголовке конструктора операций.<xref:System.Activities.Statements.State.DisplayName%2A> используется в строке навигатора, которая отображается в верхней части конструктора рабочих процессов.<br /><br /> Несмотря на то, что свойство <xref:System.Activities.Statements.State.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Указывает действие, которое выполняется при переходе в это состояние.Если действие <xref:System.Activities.Statements.State> развернуто, это значение может быть задано с помощью перетаскивания действия из **области элементов** и помещения его в разделе **Вход** состояния.|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|Указывает действие, которое выполняется при переходе из этого состояния.Если действие <xref:System.Activities.Statements.State> развернуто, это значение может быть задано с помощью перетаскивания действия из **области элементов** и помещения его в разделе **Выход** состояния.|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Перечисляет возможные переходы, исходящие из <xref:System.Activities.Statements.State>.Каждый элемент в списке имеет соединение со связанным <xref:System.Activities.Statements.Transition> и назначение <xref:System.Activities.Statements.State>.При щелчке по ссылке конструктор переключится в расширенное представление для <xref:System.Activities.Statements.Transition> или <xref:System.Activities.Statements.State>.|  
  
## См. также  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [Переход](../workflow-designer/transition-activity-designer.md)