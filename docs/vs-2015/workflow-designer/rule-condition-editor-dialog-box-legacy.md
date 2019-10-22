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
ms.openlocfilehash: 93aef1e4466bd88d87ebce71161dcd1665178317
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663354"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Диалоговое окно «Редактор условий для правила» (для прежних версий)
В этом разделе описывается использование диалогового окна **Редактор условий правил** в [!INCLUDE[wfd1](../includes/wfd1-md.md)] устаревших версий. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Условия декларативного правила создаются и изменяются с помощью диалогового окна **Редактор условий правил** . Эти условия правила представляются как свойства в следующих готовых действиях Windows Workflow Foundation:

- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

- [статемачиневоркфловактивити](http://go.microsoft.com/fwlink?LinkID=65045)

  Доступ к диалоговому окну **Редактор условий правил** можно получить с помощью [диалогового окна Выбор условия (прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md).

  В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна **Редактор условий правил** .

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Выполняет**|Введите выражение для условия правила.|
|**Хорошо**|Нажмите для сохранения условия правила.|

## <a name="entering-condition-expressions"></a>Введите выражения условий.
 Выражения условий вводятся как текст. Это можно ввести **.** в редактор для ссылки на поля, свойства и методы, используемые в рабочем процессе, с помощью меню, похожего на IntelliSense. Либо можно прямо ввести имя члена рабочего процесса. К условию можно добавить логические операторы, например AND ("И"), OR ("ИЛИ") и NOT ("НЕ"). Также можно добавлять предикаты. Предикат - это бинарный оператор и два операнда. Поддерживаются бинарные операторы: **==** , **>** , **\<** , **>=** и **<=** . Поддерживаемые операнды - константа арифметическая функция и члены с соответствующей областью действия.

 Можно указать тип для сравнения, а также сравнить со **значением NULL** или с пустой строкой. Можно создать вложенные вызовы к членам в переменных, которые содержат сложный тип, например `this.Address.State == "WA"`.

 Редактор условий для правил поддерживает следующие операторы:

- Реляционные операторы: ==, =, !=

- Операторы сравнения: <, \< =, >, > =

- Арифметические операторы: +, -, *, /, MOD

- Логические операторы: и, & & или, &#124; &#124;, not,!

- Побитовые операторы: &,&#124;

  Приоритет оператора выражения определяется правилами приоритета операторов языка C#.

  Редактор условий для правил поддерживает следующие числовые выражения:

  this.i == 1D (вычисляется как 1.0)

  this.i == 1E1 (вычисляется как 10.0)

  this.i == 1L (вычисляется как long)

  this.i == 1M (вычисляется как десятичное)

  this.i == 1F (вычисляется как единственный)

  this.i == 1U (вычисляется как unsigned int)

  Дополнительные сведения об условиях см. [в разделе Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>См. также раздел
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039) [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049) [SELECT условие (прежние версии)](../workflow-designer/select-condition-dialog-box-legacy.md) [Использование условий в рабочих](http://go.microsoft.com/fwlink?LinkID=65009) процессах [устаревший конструктор для Windows Workflow Справка по пользовательскому интерфейсу Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)