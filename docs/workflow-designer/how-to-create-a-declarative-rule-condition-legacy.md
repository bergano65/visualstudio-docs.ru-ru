---
title: 'Как: создать условие декларативного правила (для прежних версий) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e8b1d1220f11d27ee193e3e82168f4c10558d86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Как создать условие декларативного правила (для прежних версий)
В этом разделе описывается объявление условия правила с помощью конструктора рабочих процессов прежних версий Windows, предназначенное [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Условный оператор оценивает значение **True** или **False**. Условие декларативного правила — условный оператор, который создается с помощью [условие редактора диалогового окна правила (для прежних версий)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) и хранятся в виде XML с рабочим процессом. Он может включать предикаты, которые сравнивают состояние рабочего процесса и булеву алгебру, в которой объединено множество предикатов.

 Условия декларативного правила используются в следующих готовых действиях Windows Workflow Foundation:

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [У операции WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Для создания условия декларативного правила используется Редактор условий для правил

1.  В действии **свойства** окно, нажмите кнопку **условие** свойство или **UntilCondition** свойства, в зависимости от активности.

2.  Выберите **условие декларативного правила** из списка для свойства.

3.  Разверните **условие** или **UntilCondition** свойство.

4.  Нажмите кнопку **ConditionName** свойство.

5.  Нажмите кнопку **ConditionName** многоточие **[...]**  Открытие **выбрать условие** диалоговое окно.

6.  Нажмите кнопку **новое условие** Открытие **редактор условий для правил** диалоговое окно.

7.  Введите выражение для условия в **условие** текстовое поле.

     Сведения о способах создания выражения условия в разделе [условие редактора диалогового окна правила (для прежних версий)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8.  После создания выражения условия нажмите кнопку **ОК** закрыть диалоговое окно и создать условие правила с назначенным именем.

     **Выбрать условие** откроется диалоговое окно.

     Сведения об использовании **выбрать условие** диалоговое окно, в разделе [условие диалоговое окно Выбор (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>См. также

- [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)
- [С помощью ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)
- [Использование действия IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)
- [С помощью операции репликатора](http://go.microsoft.com/fwlink?LinkID=65080)
- [С помощью While действия](http://go.microsoft.com/fwlink?LinkID=65091)
- [Диалоговое окно "Редактор условий для правила" (для прежних версий)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)
- [Диалоговое окно "Выбор условия" (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009)