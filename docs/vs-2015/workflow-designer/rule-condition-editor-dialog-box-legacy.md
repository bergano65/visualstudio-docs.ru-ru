---
title: Диалоговое окно "Редактор условий правил" (устаревшая) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00df917b05f5073634b0956a0b44e5b0fc6026a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846336"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Диалоговое окно «Редактор условий для правила» (для прежних версий)
В этом разделе описывается использование диалогового окна **Редактор условий правил** в устаревшей версии [!INCLUDE[wfd1](../includes/wfd1-md.md)] . [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Условия декларативного правила создаются и изменяются с помощью диалогового окна **Редактор условий правил** . Эти условия правила представляются как свойства в следующих готовых действиях Windows Workflow Foundation:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

  Доступ к диалоговому окну **Редактор условий правил** можно получить с помощью [диалогового окна Выбор условия (прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md).

  В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна **Редактор условий правил** .

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Выполняет**|Введите выражение для условия правила.|
|**OK**|Нажмите для сохранения условия правила.|

## <a name="entering-condition-expressions"></a>Введите выражения условий.
 Выражения условий вводятся как текст. Это можно ввести **.** в редактор для ссылки на поля, свойства и методы, используемые в рабочем процессе, с помощью меню, похожего на IntelliSense. Либо можно прямо ввести имя члена рабочего процесса. К условию можно добавить логические операторы, например AND ("И"), OR ("ИЛИ") и NOT ("НЕ"). Можно также добавить предикаты. Предикат - это бинарный оператор и два операнда. Поддерживаются бинарные операторы: **==** ,, **>** **\<**, **>=** и **<=** . Поддерживаемые операнды - константа арифметическая функция и члены с соответствующей областью действия.

 Можно указать тип для сравнения, а также сравнить со **значением NULL** или с пустой строкой. Можно создать вложенные вызовы к членам в переменных, которые содержат сложный тип, например `this.Address.State == "WA"`.

 Редактор условий для правил поддерживает следующие операторы:

- Реляционные операторы: ==, =, !=

- Операторы сравнения: <, \<=, > , >=

- Арифметические операторы: +, -, *, /, MOD

- Логические операторы: и,  && или,  &#124;&#124;, NOT,!

- Побитовые операторы: &, &#124;

  Приоритет оператора выражения определяется правилами приоритета операторов языка C#.

  Редактор условий для правил поддерживает следующие числовые выражения:

  this.i == 1D (вычисляется как 1.0)

  this.i == 1E1 (вычисляется как 10.0)

  this.i == 1L (вычисляется как long)

  this.i == 1M (вычисляется как десятичное)

  this.i == 1F (вычисляется как единственный)

  this.i == 1U (вычисляется как unsigned int)

  Дополнительные сведения об условиях см. [в разделе Использование условий в рабочих процессах](https://msdn2.microsoft.com/library/bb628447.aspx).

## <a name="see-also"></a>См. также:
 [IfElseActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx) [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx) [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx) [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx) [SELECT условие (устаревший)](../workflow-designer/select-condition-dialog-box-legacy.md) [Использование условий в рабочих процессах](https://msdn2.microsoft.com/library/bb628447.aspx) [устаревший конструктор для Windows Workflow Foundation справки по пользовательскому интерфейсу](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
