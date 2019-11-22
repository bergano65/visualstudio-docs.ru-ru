---
title: Rule Set Editor Dialog Box (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83cdd4f549655be524abdd2a4708b316f6747b3e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302761"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Диалоговое окно «Редактор набора правил» (для прежних версий)
This topic describes how use the **Rule Set Editor** dialog box in the legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 The **Rule Set Editor** dialog box is used to create and modify [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) rule sets, which are serialized to a .rules file.

> [!NOTE]
> If you want to open the .rules file with the **XML Editor with encoding**, you must first close the associated designer window for the workflow or activity.

 For information about how to access the **Rule Set Editor** dialog box, see [How to: Create a PolicyActivity Rule Set (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> Редактор правил [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий, используемый для работы с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], не поддерживает настройку для различных версий.

 The following table describes the user interface (UI) elements of the **Rule Set Editor** dialog box.

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Add Rule**|Добавляет новое определение правила в набор правил.|
|**Удалить**|Удаляет выбранное правило из набора правил.|
|**Chaining**|Задает тип прямой логической цепочки для использования с набором правил. Доступны следующие варианты:<br /><br /> -   **Full Chaining**, which specifies to use all forward chaining mechanisms: implicit, method attributing, and explicit using an **Update** function.<br />-   **Sequential**, which specifies not to use any forward chaining.<br />-   **Explicit Update Only**, which specifies to only perform forward chaining on **Update** actions.<br /><br /> For more information about forward chaining, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).|
|**Name**|Заголовок столбца со списком набора правил. Нажмите, чтобы отсортировать список правил по имени.|
|**Priority**|Заголовок столбца со списком набора правил. Нажмите, чтобы отсортировать список правил по приоритету.|
|**Reevaluation**|Заголовок столбца со списком набора правил. Нажмите, чтобы отсортировать список правил по типу повторной оценки.|
|**Rule Preview**|Заголовок столбца со списком набора правил. Нажмите, чтобы отсортировать список правил по условию предварительного просмотра правила и действиям.|
|**Name.**|Введите имя правила.|
|**Priority:**|Введите приоритет правила. Приоритет по умолчанию равен 0.|
|**Reevaluation:**|Задает тип повторной оценки правила для использования с правилом. Доступны следующие варианты:<br /><br /> -   **Always**, which causes the rule to be reevaluated as needed.<br />-   **Never**, which causes the rule to never be reevaluated. В этом случае правило выполняется только один раз.|
|**Active**|Включите, чтобы сделать это правило активным.|
|**Condition:**|Введите выражение для условия правила. Описание синтаксиса выражений см. в разделе "Ввод выражений условия и действия" на этой странице.|
|**Then Actions:**|Введите выражение для действий THEN. Описание синтаксиса выражений см. в разделе "Ввод выражений условия и действия" на этой странице.|
|**Else Actions:**|Введите выражение для действий ELSE. Описание синтаксиса выражений см. в разделе "Ввод выражений условия и действия" на этой странице.|
|**OK**|Нажмите для сохранения набора правил в файл RULES.|

 For more information about rule sets, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Ввод выражений условия и действия
 You enter expressions for the Condition and the Then and Else actions as text in their respective text boxes in the **Rule Set Editor** dialog box. You can type **this.** into the editor to reference fields, properties and methods used in the workflow, using an IntelliSense-type of menu. Либо можно прямо ввести имя члена рабочего процесса. Можно вызвать статические методы для ссылочных типов, для этого введите имя класса, далее имя метода.

 К условию можно добавить логические операторы, например AND ("И"), OR ("ИЛИ") и NOT ("НЕ"). Также можно добавлять предикаты. Предикат - это бинарный оператор и два операнда. The binary operators supported are ==, >, \<, >=, and <=. Поддерживаемые операнды - константа арифметическая функция и члены с соответствующей областью действия.

 You can specify the type for the comparison, and you can compare to **null** or an empty string. Можно вложить вызовы к членам в переменные, которые содержат сложный тип, например `this.Address.State == "WA"`.

 Выражения поддерживают следующие операторы:

- Реляционные операторы: ==, =, !=

- Comparison operators: <, \<=, >, >=

- Арифметические операторы: +, -, *, /, MOD

- Logical operators: AND, &&, OR, &#124;&#124;, NOT, !

- Bitwise operators: &, &#124;

  Приоритет оператора выражения определяется правилами приоритета операторов языка C#.

  For more information about conditions, see [Using Conditions in Workflows](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Функции Halt и Update
 **Then Actions:** and **Else Actions:** expressions support **Halt** and **Update** functions. To use the **Halt** function, type **Halt** into a **Then Action:** or **Else Action:** text box. The **Halt** action causes rule set execution to stop immediately, and control returns to the calling code. You use the **Update** function with forward chaining.

 An **Update** statement can be expressed in the editor in one of two forms; both forms are shown in the following example:

```
Update(this.Address.State)
Update("this/Address/State")
```

 For more information about using **Update** with forward chaining, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>См. также раздел
 [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004) [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009)