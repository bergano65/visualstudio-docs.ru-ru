---
title: "Диалоговое окно «Редактор условий для правил» (для прежних версий) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords: Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 98a42547786e15815ef760e9f397c3c469c4a1a1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Диалоговое окно «Редактор условий для правила» (для прежних версий)
В этом разделе описывается использование **редактор условий для правил** диалоговое окно в прежних [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
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
|**ХОРОШО**|Нажмите для сохранения условия правила.|  
  
## <a name="entering-condition-expressions"></a>Введите выражения условий.  
 Выражения условий вводятся как текст. Можно ввести **это.** в редактор для ссылки на поля, свойства и методы, используемые в рабочем процессе с помощью меню типа IntelliSense. Либо можно прямо ввести имя члена рабочего процесса. К условию можно добавить логические операторы, например AND ("И"), OR ("ИЛИ") и NOT ("НЕ"). Также можно добавлять предикаты. Предикат - это бинарный оператор и два операнда. Используются следующие бинарные операторы поддерживается  **==** ,  **>** ,  **\<** ,  **>=** , и  **<=** . Поддерживаемые операнды - константа арифметическая функция и члены с соответствующей областью действия.  
  
 Можно указать тип для сравнения, сравнивать можно со **null** или является пустой строкой. Можно создать вложенные вызовы к членам в переменных, которые содержат сложный тип, например `this.Address.State == "WA"`.  
  
 Редактор условий для правил поддерживает следующие операторы:  
  
-   Реляционные операторы: ==, =, !=  
  
-   Операторы сравнения: <, \<=, >, > =  
  
-   Арифметические операторы: +, -, *, /, MOD  
  
-   Логические операторы: И, & &, OR, &#124; &#124; NOT,!  
  
-   Битовые операторы: &, &#124;  
  
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
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [У операции WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Диалоговое окно выберите условие (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Справка по интерфейсу пользователя конструктора прежних версий для Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)