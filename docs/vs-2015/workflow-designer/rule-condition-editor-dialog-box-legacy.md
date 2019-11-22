---
title: Rule Condition Editor Dialog Box (Legacy) | Microsoft Docs
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
ms.openlocfilehash: a632b90e89e58c26ec72083fe3f4ed9223826dae
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302848"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Диалоговое окно «Редактор условий для правила» (для прежних версий)
This topic describes how use the **Rule Condition Editor** dialog box in the legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 You create and modify declarative rule conditions by using the **Rule Condition Editor** dialog box. Эти условия правила представляются как свойства в следующих готовых действиях Windows Workflow Foundation:

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

  You access the **Rule Condition Editor** dialog box by using the [Select Condition Dialog Box (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

  The following table describes the user interface (UI) elements of the **Rule Condition Editor** dialog box.

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Condition:**|Введите выражение для условия правила.|
|**OK**|Нажмите для сохранения условия правила.|

## <a name="entering-condition-expressions"></a>Введите выражения условий.
 Выражения условий вводятся как текст. You can type **this.** into the editor to reference fields, properties, and methods used in the workflow, using an IntelliSense-like menu. Либо можно прямо ввести имя члена рабочего процесса. К условию можно добавить логические операторы, например AND ("И"), OR ("ИЛИ") и NOT ("НЕ"). Также можно добавлять предикаты. Предикат - это бинарный оператор и два операнда. The binary operators supported are **==** , **>** , **\<** , **>=** , and **<=** . Поддерживаемые операнды - константа арифметическая функция и члены с соответствующей областью действия.

 You can specify the type for the comparison, and you can compare to **null** or an empty string. Можно создать вложенные вызовы к членам в переменных, которые содержат сложный тип, например `this.Address.State == "WA"`.

 Редактор условий для правил поддерживает следующие операторы:

- Реляционные операторы: ==, =, !=

- Comparison operators: <, \<=, >, >=

- Арифметические операторы: +, -, *, /, MOD

- Logical operators: AND, &&, OR, &#124;&#124;, NOT, !

- Bitwise operators: &, &#124;

  Приоритет оператора выражения определяется правилами приоритета операторов языка C#.

  Редактор условий для правил поддерживает следующие числовые выражения:

  this.i == 1D (вычисляется как 1.0)

  this.i == 1E1 (вычисляется как 10.0)

  this.i == 1L (вычисляется как long)

  this.i == 1M (вычисляется как десятичное)

  this.i == 1F (вычисляется как единственный)

  this.i == 1U (вычисляется как unsigned int)

  For more information about conditions, see [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>См. также раздел
 [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039) [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049) [Select Condition Dialog Box (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md) [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009) [Legacy Designer for Windows Workflow Foundation UI Help](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)