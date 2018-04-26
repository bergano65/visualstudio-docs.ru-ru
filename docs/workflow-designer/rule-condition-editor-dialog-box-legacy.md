---
title: Конструктор рабочих процессов - диалоговое окно «Редактор условий для правил» (для прежних версий)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f723894f175cbf031c3a2ac61ed9eaec8e1c94f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Диалоговое окно «Редактор условий для правила» (для прежних версий)

В этом разделе описывается использование **редактор условий для правил** диалоговое окно в конструкторе рабочих процессов прежних версий Windows. Используйте конструктор рабочих процессов прежних версий, для целевой платформы .NET Framework 3.5 или WinFX.

Создание и изменение условий декларативного правила с помощью **редактор условий для правил** диалоговое окно. Эти условия правила представляются как свойства в следующих готовых действиях Windows Workflow Foundation:

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [У операции WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

Доступ к **редактор условий для правил** диалоговое окно с помощью [условие диалоговое окно Выбор (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md).

В следующей таблице описаны элементы пользовательского интерфейса (UI) **редактор условий для правил** диалоговое окно.

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Условие:**|Введите выражение для условия правила.|
|**OK**|Нажмите для сохранения условия правила.|

## <a name="entering-condition-expressions"></a>Введите выражения условий.

Выражения условий вводятся как текст. Можно ввести **это.** в редактор для ссылки на поля, свойства и методы, используемые в рабочем процессе с помощью меню типа IntelliSense. Либо можно прямо ввести имя члена рабочего процесса. К условию можно добавить логические операторы, например AND ("И"), OR ("ИЛИ") и NOT ("НЕ"). Также можно добавлять предикаты. Предикат - это бинарный оператор и два операнда. Используются следующие бинарные операторы поддерживается **==**, **>**, **\<**, **>=**, и **<=**. Поддерживаемые операнды - константа арифметическая функция и члены с соответствующей областью действия.

Можно указать тип для сравнения, сравнивать можно со **null** или является пустой строкой. Можно создать вложенные вызовы к членам в переменных, которые содержат сложный тип, например `this.Address.State == "WA"`.

Редактор условий для правил поддерживает следующие операторы:

-   Реляционные операторы: ==, =, !=

-   Операторы сравнения: <, \<=, >, > =

-   Арифметические операторы: +, -, \*, /, MOD

-   Логические операторы: И, & &, OR, &#124; &#124;, NOT,!

-   Битовые операторы: &,&#124;

Приоритет оператора выражения определяется правилами приоритета операторов языка C#.

Редактор условий для правил поддерживает следующие числовые выражения:

this.i == 1D (вычисляется как 1.0)

this.i == 1E1 (вычисляется как 10.0)

this.i == 1L (вычисляется как long)

this.i == 1M (вычисляется как десятичное)

this.i == 1F (вычисляется как единственный)

this.i == 1U (вычисляется как unsigned int)

Дополнительные сведения об условиях см. в разделе [использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>См. также

- [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)
- [У операции WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)
- [Диалоговое окно "Выбор условия" (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009)
- [Справка по интерфейсу пользователя конструктора прежних версий для Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)