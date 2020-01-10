---
title: Как создать условие декларативного правила (устаревшее) | Документация Майкрософт
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849334"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Как создать условие декларативного правила (для прежних версий)
В этом разделе описывается объявление условия правила с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Оператор Condition принимает **значение true** или **false**. Условие декларативного правила — это оператор условия, созданный с помощью [диалогового окна Редактор условий правил (устаревший)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) и хранимый в виде XML с рабочим процессом. Он может включать предикаты, которые сравнивают состояние рабочего процесса и булеву алгебру, в которой объединено множество предикатов.

 Условия декларативного правила используются в следующих готовых действиях Windows Workflow Foundation:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [статемачиневоркфловактивити](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Для создания условия декларативного правила используется Редактор условий для правил

1. В окне **свойств** действия выберите свойство **Condition** или свойство **UntilCondition** в зависимости от действия.

2. Выберите **Условие декларативного правила** из списка для свойства.

3. Разверните свойство **Condition** или **UntilCondition** .

4. Щелкните свойство **кондитионнаме** .

5. Щелкните **кондитионнаме** многоточие **[...]** , чтобы открыть диалоговое окно **Выбор условия** .

6. Нажмите кнопку **создать условие** , чтобы открыть диалоговое окно **Редактор условий правил** .

7. Введите выражение для условия в текстовом поле **условие** .

     Дополнительные сведения о создании выражений условий см. в разделе [диалоговое окно редактора условий правил (прежние версии)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Завершив создание выражения условия, нажмите кнопку **ОК** , чтобы закрыть диалоговое окно и создать условие правила с назначенным именем.

     Откроется диалоговое окно **Выбор условия** .

     Дополнительные сведения об использовании диалогового окна **Выбор** условия см. в разделе [диалоговое окно «Выбор условия» (устаревшая)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>См. также раздел
 [Устаревшие действия рабочего процесса](../workflow-designer/legacy-workflow-activities.md) [с использованием ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx) [с помощью действия IfElseBranchActivity](https://msdn2.microsoft.com/library/bb628465.aspx) с [помощью действия репликатора](https://msdn2.microsoft.com/library/bb628544.aspx) в [Using the While Activity](https://msdn2.microsoft.com/library/bb628552.aspx) [диалоговом окне "Редактор условий правил действий" (устаревшая) ](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [Диалоговое окно "Выбор условия" (устаревшее)](../workflow-designer/select-condition-dialog-box-legacy.md) [с использованием условий в рабочих процессах](https://msdn2.microsoft.com/library/bb628447.aspx)
