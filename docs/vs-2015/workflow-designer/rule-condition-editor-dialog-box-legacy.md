---
title: Диалоговое окно «Редактор условий для правил» (для прежних версий) | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8237c8e29007d010cd99e4323bf8e88a23b7e9fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006831"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Диалоговое окно «Редактор условий для правила» (для прежних версий)
Здесь описывается, как использовать **редактор условий для правил** диалогового окна в прежних версий [!INCLUDE[wfd1](../includes/wfd1-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Создание и изменение условий декларативного правила с помощью **редактор условий для правил** диалоговое окно. Эти условия правила представляются как свойства в следующих готовых действиях Windows Workflow Foundation:  
  
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
  Доступ к **редактор условий для правил** диалоговое окно с помощью [выберите условие диалоговое окно (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
  В следующей таблице описаны элементы пользовательского интерфейса (UI) **редактор условий для правил** диалоговое окно.  
  
|Элемент пользовательского интерфейса|Описание|  
|----------------|-----------------|  
|**Условие:**|Введите выражение для условия правила.|  
|**OK**|Нажмите для сохранения условия правила.|  
  
## <a name="entering-condition-expressions"></a>Введите выражения условий.  
 Выражения условий вводятся как текст. Можно ввести **это.** в редактор для ссылки на поля, свойства и методы, используемые в рабочем процессе с помощью меню типа IntelliSense. Либо можно прямо ввести имя члена рабочего процесса. К условию можно добавить логические операторы, например AND ("И"), OR ("ИЛИ") и NOT ("НЕ"). Также можно добавлять предикаты. Предикат - это бинарный оператор и два операнда. Двоичный поддерживаются следующие операторы: **==** , **>** , **\<** , **>=** , и **<=** . Поддерживаемые операнды - константа арифметическая функция и члены с соответствующей областью действия.  
  
 Можно указать тип для сравнения, и можно сравнить **null** или является пустой строкой. Можно создать вложенные вызовы к членам в переменных, которые содержат сложный тип, например `this.Address.State == "WA"`.  
  
 Редактор условий для правил поддерживает следующие операторы:  
  
- Реляционные операторы: ==, =, !=  
  
- Операторы сравнения: <, \<=, >, > =  
  
- Арифметические операторы: +, -, *, /, MOD  
  
- Логические операторы И, &AMP; &AMP;, OR, &AMP;#124; &AMP;#124;, NOT,!  
  
- Побитовые операторы: &,&#124;  
  
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
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Выберите диалоговое окно «условие» (для прежних версий)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Использование условий в рабочих процессах](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Справка по интерфейсу пользователя конструктора прежних версий для Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)