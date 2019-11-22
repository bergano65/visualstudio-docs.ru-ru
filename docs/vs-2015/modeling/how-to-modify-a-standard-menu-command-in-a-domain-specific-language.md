---
title: 'How to: Modify a Standard Menu Command in a Domain-Specific Language | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 989367d395abb56e4f57c4aa2694b5f4ef17fb6e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300870"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Практическое руководство. Изменение стандартной команды меню в доменном языке
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Поведение некоторых стандартных команд, определенных в доменном языке автоматически, можно изменять. For example, you could modify **Cut** so that it excludes sensitive information. Для этого необходимо переопределить методы в классе наборов команд. Эти классы определяются в файле CommandSet.cs проекта DslPackage project и являются производными от класса <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

 Таким образом, чтобы изменить команду:

1. [Discover what commands you can modify](#what).

2. [Create a partial declaration of the appropriate command set class](#extend).

3. [Override the ProcessOnStatus and ProcessOnMenu methods](#override) for the command.

   Данная процедура описана в этом разделе.

> [!NOTE]
> If you want to create your own menu commands, see [How to: Add a Command to the Shortcut Menu](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what"></a> What commands can you modify?

#### <a name="to-discover-what-commands-you-can-modify"></a>Поиск команд, доступных для изменения

1. In the `DslPackage` project, open `GeneratedCode\CommandSet.cs`. This C# file can be found in Solution Explorer as a subsidiary of `CommandSet.tt`.

2. Find classes in this file whose names end with "`CommandSet`", for example `Language1CommandSet` and `Language1ClipboardCommandSet`.

3. В каждом классе наборов команд введите "`override`" и пробел. IntelliSense отобразит список методов, которые можно переопределить. Каждая команда имеет пару методов, имена которых начинаются с "`ProcessOnStatus`" и "`ProcessOnMenu`".

4. Запомните, какой класс наборов команд содержит команду, подлежащую изменению.

5. Закройте файл без сохранения изменений.

    > [!NOTE]
    > Обычно генерируемые файлы не редактируются. При следующей генерации файлов все изменения будут утеряны.

## <a name="extend"></a> Extend the appropriate command set class
 Создайте новый файл, содержащий частичное описание класса наборов команд.

#### <a name="to-extend-the-command-set-class"></a>Расширение класса наборов команд

1. В Обозревателе решений в проекте DslPackage откройте папку GeneratedCode, найдите раздел CommandSet.tt и откройте созданный в нем файл CommandSet.cs. Запомните пространство имен и имя первого определенного здесь класса. Например:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. In **DslPackage**, create a folder named **Custom Code**. In this folder, create a new class file named `CommandSet.cs`.

3. В новом файле напишите частичное объявление, используя то же пространство имен и имя, что и в созданном частичном классе. Пример:

    ```
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

     **Note** If you used the class file template to create the new file, you must correct both the namespace and the class name.

## <a name="override"></a> Override the command methods
 Most commands have two associated methods: The method with a name like `ProcessOnStatus`... determines whether the command should be visible and enabled. Она вызывается, когда пользователь щелкает схему правой кнопкой мыши, и должна выполняться быстро и не вносить изменений. `ProcessOnMenu`... is called when the user clicks the command, and should perform the function of the command. Возможно, потребуется переопределение одного или двух этих методов.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Изменение условий отображения команды в меню
 Override the ProcessOnStatus... method. Он должен задавать свойства Visible и Enabled своего параметра MenuCommand. Обычно команда проверяет this.CurrentSelection, чтобы определить, применяется ли команда к выбранным элементам, а также может проверить их свойства, чтобы определить возможность применения команды в их текущем состоянии.

 Как правило, свойство Visible должно определяться выбранными элементами. Свойство Enabled, определяющее цвет отображения команды в меню (черный или серый), должно зависеть от текущего состояния выделения.

 В следующем примере элемент меню "Удалить" отключается, когда пользователь выбирает больше одной фигуры.

> [!NOTE]
> Этот метод не влияет на доступность команды при нажатии клавиши. Например, отключение элемента меню "Удалить" не запрещает вызов команды с помощью клавиши Delete.

```
/// <summary>
/// Called when user right-clicks on the diagram or clicks the Edit menu.
/// </summary>
/// <param name="command">Set Visible and Enabled properties.</param>
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)
{
  // Default settings from the base method.
  base.ProcessOnStatusDeleteCommand(command);
  if (this.CurrentSelection.Count > 1)
  {
    // If user has selected more than one item, Delete is greyed out.
    command.Enabled = false;
  }
}
```

 Рекомендуется вначале вызвать базовый метод, чтобы обработать все случаи и настройки, которые вас не беспокоят.

 Метод ProcessOnStatus не должен создавать, удалять или обновлять элементы в Магазине.

### <a name="to-change-the-behavior-of-the-command"></a>Изменение поведения команды
 Override the ProcessOnMenu... method. В следующем примере код запрещает пользователю удалять больше одного элемента за один раз даже с помощью клавиши Delete.

```
/// <summary>
/// Called when user presses Delete key
/// or clicks the Delete command on a menu.
/// </summary>
protected override void ProcessOnMenuDeleteCommand()
{
  // Allow users to delete only one thing at a time.
  if (this.CurrentSelection.Count <= 1)
  {
    base.ProcessOnMenuDeleteCommand();
  }
}
```

 Если код вносит в Магазин такие изменения, как создание, удаление или обновление элементов и ссылок, необходимо делать это внутри транзакции. For more information, see [How to Create and Update model elements](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="writing-the-code-of-the-methods"></a>Написание кода методов
 В этих методах часто используются следующие фрагменты:

- `this.CurrentSelection` Фигура, которую пользователь щелкает правой кнопкой мыши, всегда включается в этот список фигур и соединителей. Если пользователь щелкает пустую область схемы, схема становится единственным членом списка.

- `this.IsDiagramSelected()` - `true` if the user clicked a blank part of the diagram.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` - the user did not select multiple shapes

- `this.SingleSelection` - the shape or diagram that the user right-clicked

- `shape.ModelElement as MyLanguageElement` - the model element represented by a shape.

  For more information about how to navigate from element to element and about how to create objects and links, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>См. также раздел
 <xref:System.ComponentModel.Design.MenuCommand> [Writing Code to Customise a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md) [How to: Add a Command to the Shortcut Menu](../modeling/how-to-add-a-command-to-the-shortcut-menu.md) [Walkthrough: Getting Information from a Selected Link](../misc/walkthrough-getting-information-from-a-selected-link.md) [How VSPackages Add User Interface Elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md) [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [VSCT XML Schema Reference](../extensibility/vsct-xml-schema-reference.md)
