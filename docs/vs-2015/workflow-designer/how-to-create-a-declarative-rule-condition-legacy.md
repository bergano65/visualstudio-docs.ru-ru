---
title: Практическое руководство. Создать условие декларативного правила (для прежних версий) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbdcc268b71f2926307b500126840391dd5308fd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039534"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Практическое руководство. Создание условия декларативного правила (для прежних версий)
В этом разделе описывается объявление условия правила с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Условный оператор оценивает значение **True** или **False**. Условие декларативного правила-это условный оператор, который создается с помощью [правило условие диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) и хранятся в виде XML с рабочим процессом. Он может включать предикаты, которые сравнивают состояние рабочего процесса и булеву алгебру, в которой объединено множество предикатов.  
  
 Условия декларативного правила используются в следующих готовых действиях Windows Workflow Foundation:  
  
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Для создания условия декларативного правила используется Редактор условий для правил  
  
1. В действии **свойства** окно, нажмите кнопку **условие** свойство или **UntilCondition** свойство зависимости от действия.  
  
2. Выберите **условие декларативного правила** из списка для свойства.  
  
3. Разверните **условие** или **UntilCondition** свойство.  
  
4. Нажмите кнопку **ConditionName** свойство.  
  
5. Нажмите кнопку **ConditionName** многоточие **[...]**  открыть **выбрать условие** диалоговое окно.  
  
6. Нажмите кнопку **новое условие** открыть **редактор условий для правил** диалоговое окно.  
  
7. Введите выражение для условия в **условие** текстовое поле.  
  
     Сведения о создании выражений условия см. в разделе [правило условие диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8. После завершения создания выражения условия нажмите кнопку **ОК** чтобы закрыть диалоговое окно и создать условие правила с назначенным именем.  
  
     **Выбрать условие** откроется диалоговое окно.  
  
     Сведения об использовании **выбрать условие** диалоговом окне см. в разделе [выберите условие диалоговое окно (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>См. также  
 [Действия рабочего процесса прежних версий](../workflow-designer/legacy-workflow-activities.md)   
 [Использование ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Использование действия IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Использование действия Replicator](http://go.microsoft.com/fwlink?LinkID=65080)   
 [С помощью While действия](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Диалоговое окно «Редактор условий для правил» (для прежних версий)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Выберите диалоговое окно «условие» (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009)