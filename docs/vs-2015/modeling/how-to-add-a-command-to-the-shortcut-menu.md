---
title: 'How to: Add a Command to the Shortcut Menu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: cd550399-05fc-4dbf-be4c-f5094bb752ce
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8d5373ae27797aa3bfe4627fb84ce393dce9e910
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300884"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Практическое руководство. Добавление команды в контекстное меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы пользователи могли выполнять задачи, характерные для вашего доменного языка (DSL), можно добавить в него команды меню. Команды отображаются в контекстном меню, когда пользователь нажимает схему правой кнопкой мыши. Команду можно настроить таким образом, чтобы она появлялась в меню только при определенных обстоятельствах. Например, можно сделать команду видимой, только когда пользователь выбирает определенные типы элементов или элементы в определенных состояниях.

 В проекте DslPackage эта задача решается выполнением следующих действий.

1. [Declare the command in Commands.vsct](#VSCT)

2. [Update the package version number in Package.tt](#version). (Это действие выполняется при любом изменении файла Commands.vsct.)

3. [Write methods in the CommandSet class](#CommandSet) to make the command visible and to define what you want the command to do.

   For samples, see the [Visualization and Modeling SDK website](https://go.microsoft.com/fwlink/?LinkID=185579).

> [!NOTE]
> Также можно изменить поведение некоторых существующих команд, например "Вырезать", "Вставить", "Выбрать все" и "Печать", переопределив соответствующие методы в CommandSet.cs. For more information, see [How to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="defining-a-command-using-mef"></a>Определение команды с помощью MEF
 MEF (Managed Extension Framework) предлагает альтернативный метод определения команд в меню схемы. Его основная задача — включение доменного языка для расширения вами или другими сторонами. Пользователи могут выбрать установить только DSL или DSL и расширения. Кроме того, MEF уменьшает объем работы по определению команд контекстного меню после выполнения начальной работы по включению MEF в DSL.

 Используйте метод, описанный в этом разделе, если:

1. вы хотите определить команды меню или других меню, кроме контекстного (вызываемого щелчком правой кнопки мыши);

2. вы хотите настроить определенные группы команд в меню;

3. вы не хотите разрешать другим пользователям добавлять в DSL их собственные команды;

4. вы хотите определить только одну команду.

   В остальных случаях используйте для определения команд метод MEF. For more information, see [Extend your DSL by using MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="VSCT"></a> Declare the Command in Commands.Vsct
 Команды меню объявляются в файле DslPackage\Commands.vsct. Эти определения указывают на метки элементов меню и место их отображения в меню.

 The file that you edit, Commands.vsct, imports definitions from several .h files, which are located in the directory *Visual Studio SDK install path*\VisualStudioIntegration\Common\Inc. It also includes GeneratedVsct.vsct, which is generated from your DSL definition.

 For more information about .vsct files, see [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

#### <a name="to-add-the-command"></a>Добавление команды

1. In **Solution Explorer**, under the **DslPackage** project, open Commands.vsct.

2. В элементе `Commands` определите одну или несколько кнопок и группу. A *button* is an item on the menu. A *group* is a section in the menu. Чтобы определить эти элементы, добавьте следующий код:

    ```
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    > Каждая кнопка или группа идентифицируются по GUID и целочисленному идентификатору. Один и тот же GUID можно использовать при создании различных групп и кнопок, но при этом у них должны быть разные идентификаторы. The GUID names and ID names are translated to actual GUIDs and numeric IDs in the `<Symbols>` node.

3. Чтобы она загружалась только в контексте вашего доменного языка, добавьте для нее ограничение видимости. For more information, see [VisibilityConstraints Element](../extensibility/visibilityconstraints-element.md).

     Для этого добавьте в элемент `CommandTable` после элемента `Commands` следующий код:

    ```
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. Определите имена, используемые для GUID и идентификаторов. Для этого добавьте `Symbols` в элемент `CommandTable` после элемента `Commands` следующий код:

    ```
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. Замените `{000...000}` на GUID, идентифицирующий группы и элементы меню. To obtain a new GUID, use the **Create GUID** tool on the **Tools** menu.

    > [!NOTE]
    > Если вы хотите добавить сразу несколько групп или элементов меню, можно использовать один и тот же GUID. При этом необходимо использовать новые значения для `IDSymbols`.

6. В скопированном из данной процедуры коде замените собственными строками каждое вхождение следующих строк:

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="version"></a> Update the Package Version in Package.tt
 При добавлении или изменении команды обновляйте параметр `version`<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>, который применяется к классу пакета перед выпуском новой версии доменного языка.

 Поскольку класс пакета определяется в созданном классе, обновите атрибут в файле текстового шаблона, из которого создается файл Package.cs.

#### <a name="to-update-the-packagett-file"></a>Обновление файла Package.tt

1. In **Solution Explorer**, in the **DslPackage** project, in the **GeneratedCode** folder, open the Package.tt file.

2. Найдите элемент `ProvideMenuResource`.

3. Увеличьте параметр `version` атрибута, который является вторым параметром. При необходимости можно написать имя параметра, прямо указывающее на его назначение. Пример:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="CommandSet"></a> Define the Behavior of the Command
 В доменном языке уже имеются некоторые команды, внедренные в разделяемый класс, который был объявлен в файле DslPackage\GeneratedCode\CommandSet.cs. Чтобы добавить новые команды, необходимо расширить этот класс, создав новый файл с частичным объявлением того же класса. The name of the class is usually *\<YourDslName>* `CommandSet`. Лучше всего начать с проверки имени класса и его содержимого.

 Класс набора команд производится из <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

#### <a name="to-extend-the-commandset-class"></a>Расширение класса CommandSet

1. В Обозревателе решений в проекте DslPackage откройте папку GeneratedCode, найдите раздел CommandSet.tt и откройте созданный в нем файл CommandSet.cs. Запомните пространство имен и имя первого определенного здесь класса. Например:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. In **DslPackage**, create a folder that is named **Custom Code**. In this folder, create a new class file that is named `CommandSet.cs`.

3. В новом файле напишите частичное объявление, используя то же пространство имен и имя, что и в созданном частичном классе. Пример:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     **Note** If you used the class template to create the new file, you must correct both the namespace and the class name.

### <a name="extend-the-command-set-class"></a>Расширение класса наборов команд
 Код наборов команд обычно требуется для импорта следующих пространств имен:

```
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

 Исправьте пространство имен и имя класса в соответствии с созданным файлом CommandSet.cs:

```
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

 Необходимо определить два метода: один определяет, как команда будет отображаться в контекстном меню, а другой выполняет эту команду. Эти методы не переопределяются. Наоборот, их нужно зарегистрировать в списке команд.

### <a name="define-when-the-command-will-be-visible"></a>Определение условий для отображения команды
 For each command, define an `OnStatus...` method that determines whether the command will appear on the menu, and whether it will be enabled or greyed out. Set the `Visible` and `Enabled` properties of the `MenuCommand`, as shown in the following example. Этот метод вызывается для создания контекстного меню каждый раз, когда пользователь щелкает схему правой кнопкой мыши, поэтому должен работать быстро.

 В данном примере команда отображается, только когда пользователь выбирает определенный тип фигуры, и включается, только когда хотя бы один из выбранных элементов находится в определенном состоянии. Пример основан на шаблоне схем классов доменного языка, а типы ClassShape и ModelClass определяются в доменном языке.

```
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

 Следующие фрагменты часто используются в методах OnStatus:

- `this.CurrentSelection` Фигура, которую пользователь щелкает правой кнопкой мыши, всегда включается в этот список. Если пользователь щелкает пустую область схемы, схема становится единственным членом списка.

- `this.IsDiagramSelected()` - `true` if the user clicked a blank part of the diagram.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` - the user did not select multiple objects

- `this.SingleSelection` - the shape or diagram that the user right-clicked

- `shape.ModelElement as MyLanguageElement` - the model element represented by a shape.

  Как правило, свойство `Visible` должно определяться выбранным параметром, а свойство `Enabled` — состоянием выбранных элементов.

  Метод OnStatus не должен менять состояние Магазина.

### <a name="define-what-the-command-does"></a>Определение действий команды
 Для каждой команды определите метод `OnMenu...`, выполняющий необходимое действие при выборе этой команды в меню.

 Если изменения вносятся в элементы моделей, необходимо делать это внутри транзакции. For more information, see [How to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 В данном примере типы `ClassShape`, `ModelClass` и `Comment` определяются в доменном языке, который производится из шаблона схем классов DSL.

```
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 For more information about how to navigate from object to object in the model, and about how to create objects and links, see [How to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Регистрация команды
 Повторите в C# объявления значений GUID и идентификаторов, которые были сделаны в разделе "Символы" CommandSet.vsct:

```
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Use the same GUID value as you inserted in **Commands.vsct**.

> [!NOTE]
> В случае изменений в разделе "Символы" VSCT-файла для сопоставления нужно будет также изменить эти объявления. Кроме того, необходимо увеличить номер версии в Package.tt

 Зарегистрируйте команды меню как часть данного набора команд. `GetMenuCommands()` is called once when the diagram is initialized:

```
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>Тестирование команды
 Постройте и запустите доменный язык в экспериментальном экземпляре Visual Studio. Команда должна отображаться в контекстном меню в указанных вами ситуациях.

#### <a name="to-exercise-the-command"></a>Выполнение команды

1. On the **Solution Explorer** toolbar, click **Transform All Templates**.

2. Press **F5** to rebuild the solution, and start debugging the domain-specific language in the experimental build.

3. В экспериментальном построении откройте пример схемы.

4. Щелкните несколько элементов в схеме правой кнопкой мыши, чтобы проверить, правильно ли включается и отключается команда, а также правильно ли работает ее отображение или скрытие в зависимости от выбранного элемента.

## <a name="troubleshooting"></a>Устранение неполадок
 **Command does not appear in menu:**

- Пока вы не установите пакет доменного языка, команда будет отображаться только в экземплярах отладки Visual Studio. Дополнительные сведения см. в разделе [Развертывание решения на предметно-ориентированном языке](../modeling/deploying-domain-specific-language-solutions.md).

- Убедитесь, что экспериментальный язык имеет правильное расширение имени файла для этого доменного языка. Чтобы проверить расширение имени файла, откройте DslDefinition.dsl в основном экземпляре Visual Studio. Затем в Обозревателе DSL щелкните узел "Редактор" правой кнопкой мыши и выберите "Свойства". В окне "Свойства" проверьте свойство FileExtension.

- Did you [increment the package version number](#version)?

- Установите точку останова в начале метода OnStatus. Он должен останавливаться при щелчке правой кнопкой мыши по любой части схемы.

   **OnStatus method is not called**:

  - Убедитесь, что GUID и идентификаторы в коде CommandSet совпадают с идентификаторами в разделе "Символы" файла Commands.vsct.

  - В файле Commands.vsct убедитесь, что GUID и идентификаторы в каждом родительском узле указывают на правильную родительскую группу.

  - В командной строке Visual Studio введите devenv /rootsuffix exp /setup. Затем перезапустите экземпляр отладки Visual Studio.

- Выполните метод OnStatus и убедитесь, что command.Visible и command.Enabled имеют значение true.

  **Wrong menu text appears, or command appears in the wrong place**:

- Убедитесь, что комбинация GUID и идентификатора уникальна для данной команды.

- Убедитесь, что более ранние версии пакета удалены.

## <a name="see-also"></a>См. также раздел
 [Writing Code to Customise a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md) [How to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md) [Deploying Domain-Specific Language Solutions](../modeling/deploying-domain-specific-language-solutions.md)
