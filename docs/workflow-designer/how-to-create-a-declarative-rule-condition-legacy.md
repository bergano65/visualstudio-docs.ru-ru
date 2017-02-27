---
title: "Как создать условие декларативного правила (для прежних версий) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "условные операторы, декларативные условия правил"
  - "декларативные условия правил"
  - "диалоговое окно «Редактор условий для правил»"
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Как создать условие декларативного правила (для прежних версий)
В этом разделе описывается объявление условия правила с помощью средства [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Условный оператор оценивает значение **True** или значение **False**.Условие декларативного правила — это условный оператор, который создается с использованием диалогового окна [Диалоговое окно «Редактор условий для правила» \(для прежних версий\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) и сохраняется в формате XML вместе с рабочим процессом.Он может включать предикаты, которые сравнивают состояние рабочего процесса и булеву алгебру, в которой объединено множество предикатов.  
  
 Условия декларативного правила используются в следующих готовых действиях Windows Workflow Foundation:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### Для создания условия декларативного правила используется Редактор условий для правил  
  
1.  В окне действия **Свойства**, в зависимости от действия, выберите свойство **Condition** или свойство **UntilCondition**.  
  
2.  Выберите из списка для свойства пункт **Условие декларативного правила**.  
  
3.  Разверните свойство **Условие** или **UntilCondition**.  
  
4.  Выберите свойство **ConditionName**.  
  
5.  Нажмите кнопку с многоточием **ConditionName\[…\]**, чтобы открыть диалоговое окно **Выбрать условие**.  
  
6.  Выберите **Новое условие** для открытия диалогового окна **Редактор условий для правил**.  
  
7.  Введите выражение для условия в текстовое поле **Условие**.  
  
     Дополнительные сведения о создании выражений условия см. в разделе [Диалоговое окно «Редактор условий для правила» \(для прежних версий\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  После завершения создания выражения условия нажмите кнопку **ОК**, чтобы закрыть диалоговое окно и создать условие правила с назначенным именем.  
  
     Откроется диалоговое окно **Выбрать условие**.  
  
     Дополнительные сведения о порядке использования диалогового окна **Выбрать условие** см. раздел [Диалоговое окно «Выбор условия» \(для прежних версий\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## См. также  
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)   
 [Использование ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Использование действия IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Использование действия Replicator](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Использование действия While](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Диалоговое окно «Редактор условий для правила» \(для прежних версий\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Диалоговое окно «Выбор условия» \(для прежних версий\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009)