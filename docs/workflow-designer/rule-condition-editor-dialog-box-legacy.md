---
title: "Диалоговое окно &#171;Редактор условий для правила&#187; (для прежних версий) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI"
helpviewer_keywords: 
  - "диалоговое окно "Условие для правила""
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Диалоговое окно &#171;Редактор условий для правила&#187; (для прежних версий)
В этом разделе описывается использование диалогового окна **Редактор набора условий** в средстве [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий.[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Создание и изменение условий декларативного правила выполняется с использованием диалогового окна **Редактор условий для правил**.Эти условия правила представляются как свойства в следующих готовых действиях Windows Workflow Foundation:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 Доступ к диалоговому окну **Редактор условий для правил** осуществляется с помощью диалогового окна [Диалоговое окно «Выбор условия» \(для прежних версий\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
 В следующей таблице приведено описание элементов пользовательского интерфейса диалогового окна **Редактор условий для правил**.  
  
|Элемент пользовательского интерфейса|Описание|  
|------------------------------------------|--------------|  
|**Условие:**|Введите выражение для условия правила.|  
|**ОК**|Нажмите для сохранения условия правила.|  
  
## Введите выражения условий.  
 Выражения условий вводятся как текст.Можно ввести **this.** в редактор для ссылки на поля, свойства и методы, которые используются в рабочем процессе, с помощью меню типа IntelliSense.Либо можно прямо ввести имя члена рабочего процесса.К условию можно добавить логические операторы, например AND \("И"\), OR \("ИЛИ"\) и NOT \("НЕ"\).Также можно добавлять предикаты.Предикат — это двоичный оператор и два операнда.Поддерживаются следующие двоичные операторы: **\=\=**, **\>**, **\<**, **\>\=** и **\<\=**.Поддерживаемые операнды — константа арифметическая функция и члены с соответствующей областью действия.  
  
 Можно указать тип для сравнения, сравнивать можно со значением **null** или пустой строкой.Можно создать вложенные вызовы к членам в переменных, которые содержат сложный тип, например `this.Address.State == "WA"`.  
  
 Редактор условий для правил поддерживает следующие операторы:  
  
-   Реляционные операторы: \=\=, \=, \!\=  
  
-   Операторы сравнения: \<, \<\=, \>, \>\=  
  
-   Арифметические операторы: \+, \-, \*, \/, MOD  
  
-   Логические операторы: AND, &&, OR, &#124;&#124;, NOT, \!  
  
-   Битовые операторы: &, &#124;  
  
 Приоритет оператора выражения определяется правилами приоритета операторов языка C\#.  
  
 Редактор условий для правил поддерживает следующие числовые выражения:  
  
 this.i \=\= 1D \(вычисляется как 1.0\)  
  
 this.i \=\= 1E1 \(вычисляется как 10.0\)  
  
 this.i \=\= 1L \(вычисляется как long\)  
  
 this.i \=\= 1M \(вычисляется как десятичное\)  
  
 this.i \=\= 1F \(вычисляется как единственный\)  
  
 this.i \=\= 1U \(вычисляется как unsigned int\)  
  
 Дополнительные сведения об условиях см. в разделе [Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009).  
  
## См. также  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Диалоговое окно «Выбор условия» \(для прежних версий\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Справка по интерфейсу пользователя конструктора прежних версий для Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)