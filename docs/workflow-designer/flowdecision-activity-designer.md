---
title: "Конструктор действия FlowDecision | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.FlowDecision.UI"
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия FlowDecision
Узел <xref:System.Activities.Statements.FlowDecision> — это специализированный узел, который обеспечивает ветвление для передачи управления одной из двух альтернатив в зависимости от указанного условия.Если ветвление требует наличие более двух ветвей, следует вместо этого метода использовать <xref:System.Activities.Statements.FlowSwitch%601>.  
  
## Узел The FlowDecision  
 Используйте <xref:System.Activities.Statements.FlowDecision>, когда поток можно разветвить на два пути.Узел <xref:System.Activities.Statements.FlowDecision> обладает <xref:System.Activities.Statements.FlowDecision.Condition%2A> и <xref:System.Activities.Statements.FlowNode>, связанными с двумя возможными значениями: <xref:System.Activities.Statements.FlowDecision.True%2A> или <xref:System.Activities.Statements.FlowDecision.False%2A>.Выполняется оценка <xref:System.Activities.Statements.FlowDecision.Condition%2A>, причем значение этой оценки определяет следующее <xref:System.Activities.Statements.FlowNode>, которое будет обработано внутри <xref:System.Activities.Statements.Flowchart>.  
  
### Использование конструктора FlowDecision  
 Конструктор операций **FlowDecision** можно найти в категории **Блок\-схемыОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или же CTRL\+ALT\+X.\)  
  
 Конструктор **FlowDecision** можно перетащить из **Области элементов** и поместить в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] внутри конструктора событий **Блок\-схема**.Это создает <xref:System.Activities.Statements.FlowDecision>, отмеченное в **Принятие решений** в пределах действия <xref:System.Activities.Statements.Flowchart>.Наведите указатель на конструктор и квадратные дескрипторы **True** и **False**, чтобы показать две ветви.  
  
 После перетаскивания конструктора **FlowDecision** и других конструкторов в **Блок\-схему** узлы можно соединить, чтобы указать порядок выполнения.Чтобы создать связь между исходным узлом \(в том числе ветвями **True** или **False** блок\-схемы **FlowDecision**\) и узлом назначения, наведите указатель на конструктор исходного узла, что заставит появиться квадратные ярлыки на каждой его стороне.Щелкните один из них и перетащите его, удерживая кнопку мыши, к одному из маркеров, которые похожим образом появляются на целевом узле при наведении мыши.Отпустите кнопку мыши для создания ссылки между этими двумя узлами, что отмечено стрелкой от исходного к целевому конструктору.  
  
 Выражение, указывающее, что <xref:System.Activities.Statements.FlowDecision.Condition%2A> можно впечатать в окно **Условие** окна **Свойства**, щелчком там, где написано «Введите выражение VB».  
  
### Свойства FlowDecision  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.FlowDecision> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств или в области конструктора.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Да|Условие, которое определяет, какой из путей будет использован потоком данных.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Нет|Путь, предпринятый при удовлетворении условия <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Нет|Путь, предпринятый при неудовлетворении условия <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|  
  
## См. также  
 [Блок\-схема](../workflow-designer/flowchart-activity-designers.md)   
 [Блок\-схема](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)