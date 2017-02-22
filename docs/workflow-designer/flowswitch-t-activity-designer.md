---
title: "Конструктор действия FlowSwitch&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Core.Presentation.FlowSwitchLink.UI"
  - "System.Activities.Statements.FlowSwitch`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLink`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI"
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия FlowSwitch&lt;T&gt;
Действие <xref:System.Activities.Statements.FlowSwitch%601> — это условный узел, который обеспечивает ветвление потока управления на основе критерия соответствия, когда требуется более двух альтернативных ветвей.Если ветвление потока требует наличие только двух ветвей, вместо этого следует использовать действие <xref:System.Activities.Statements.FlowDecision>.  
  
## Действие FlowSwitch\<T\>  
 Действие <xref:System.Activities.Statements.FlowSwitch%601> содержит <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, возвращающее при вычислении значение типа *T* \(указанное общим параметром\).Действие также содержит набор <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, который задает уникальное сопоставление на основе возможных результатов данного вычисления набору объектов <xref:System.Activities.Statements.FlowNode>.Выполненный набор объектов <xref:System.Activities.Statements.FlowNode> является набором, в котором один из объектов типа *T* имеет значение, совпадающее со значением вычисленного <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>.Вариант <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> может быть \(дополнительно\) предоставлен для варианта, в котором совпадений не было.  
  
### Использование конструктора операций FlowSwitch\<T\>  
 Конструктор операций **FlowSwitch\<T\>** можно найти в категории **Блок\-схемаОбласти элементов**, нажав на вкладку **Область элементов** по левую сторону [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или нажмите CTRL\+ALT\+X\).  
  
 Конструктор операций **FlowSwitch\<T\>** можно перетащить из **Области элементов** и поместить в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] внутри конструктора операций **Блок\-схема**.Используйте окно **Выбор типов**, отображаемое для указания типа \(связанного в коде с <xref:System.Activities.Statements.FlowSwitch%601> с помощью их общего параметра\), полученного от вычисления <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>.Данная процедура создает действие <xref:System.Activities.Statements.FlowSwitch%601>, обозначенное как **Переключатель** в действии <xref:System.Activities.Statements.Flowchart>.<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> можно ввести в поле **Выражение** окна **Свойства** путем щелчка на тексте подсказки «Введите выражение VB».  
  
 Наведите указатель мыши на конструктор операций **FlowSwitch\<T\>** для отображения вокруг его границ квадратных маркеров, используемых для связи с <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.После перетаскивания конструктора операций **FlowSwitch\<T\>** и других конструкторов операций в область конструктора **Блок\-схема**, объекты <xref:System.Activities.Activity>, которые они представляют, можно связать друг с другом для задания порядка выполнения.Для создания одного из вариантов <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, связанного с <xref:System.Activities.Statements.FlowSwitch%601>, щелкните один из квадратных маркеров, расположенном на периметре **FlowSwitch\<T\>**, и перетащите его \(удерживая кнопку мыши\) на один из маркеров, появляющихся аналогичным образом вокруг целевого действия при наведении на него курсора мыши.Отпустите кнопку мыши и перетащите стрелку от **FlowSwitch\<T\>** к отображенному целевому конструктору, представляющему данный вариант.Значение по умолчанию для данного варианта отображается на стрелке и может быть изменено в поле **Вариант** окна **Свойства**.  
  
### Свойства FlowSwitch\<T\>  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.FlowSwitch%601> и описано их использование в конструкторе.Эти свойства можно изменить в сетке свойств или в области конструктора.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Да|Указывает выражение, вычисляемое для определения того, на какой из вариантов <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> следует переключиться в пути выполнения.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Нет|Задает уникальное сопоставление возможных результатов, полученных при вычислении <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, набору объектов <xref:System.Activities.Statements.FlowNode>.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Да|Задает сопоставление, когда вычисление <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> не совпадает ни с одним значением, содержащимся в объекте <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|  
  
## См. также  
 [Блок\-схема](../workflow-designer/flowchart-activity-designers.md)   
 [Блок\-схема](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)