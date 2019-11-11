---
title: Практическое руководство. Создание условия декларативного правила (устаревшее) | Документация Майкрософт
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
ms.openlocfilehash: d3a15aad987e46edb58da3560828c70571df2227
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663413"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Практическое руководство. Создание условия декларативного правила (для прежних версий)
В этом разделе описывается объявление условия правила с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Оператор Condition принимает **значение true** или **false**. Условие декларативного правила — это оператор условия, созданный с помощью [диалогового окна Редактор условий правил (устаревший)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) и хранимый в виде XML с рабочим процессом. Он может включать предикаты, которые сравнивают состояние рабочего процесса и булеву алгебру, в которой объединено множество предикатов.

 Условия декларативного правила используются в следующих готовых действиях Windows Workflow Foundation:

- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

- [статемачиневоркфловактивити](http://go.microsoft.com/fwlink?LinkID=65045)

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

## <a name="see-also"></a>См. также
 [Устаревшие действия рабочего процесса](../workflow-designer/legacy-workflow-activities.md) [с использованием ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066) [с помощью действия IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075) с [помощью действия репликатора](http://go.microsoft.com/fwlink?LinkID=65080) в [Using the While Activity](http://go.microsoft.com/fwlink?LinkID=65091) [диалоговом окне "Редактор условий правил действий" (устаревшая) ](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) [Диалоговое окно "Выбор условия" (устаревшее)](../workflow-designer/select-condition-dialog-box-legacy.md) [с использованием условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009)