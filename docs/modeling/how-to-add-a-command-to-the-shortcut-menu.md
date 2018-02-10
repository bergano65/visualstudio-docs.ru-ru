---
title: "Как: Добавление команды в контекстное меню | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4f65964e1d7fd4221746d8ec17a498cf9ee3a354
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Практическое руководство. Добавление команды в контекстное меню
Чтобы пользователи могли выполнять задачи, характерные для вашего доменного языка (DSL), можно добавить в него команды меню. Команды отображаются в контекстном меню, когда пользователь нажимает схему правой кнопкой мыши. Команду можно настроить таким образом, чтобы она появлялась в меню только при определенных обстоятельствах. Например, можно сделать команду видимой, только когда пользователь выбирает определенные типы элементов или элементы в определенных состояниях.  
  
 В проекте DslPackage эта задача решается выполнением следующих действий.  
  
1.  [Объявите по команде в Commands.vsct](#VSCT)  
  
2.  [Обновить номер версии пакета в Package.tt](#version). (Это действие выполняется при любом изменении файла Commands.vsct.)  
  
3.  [Написать методы в классе CommandSet](#CommandSet) сделать видимыми команды и определять, необходимых для выполнения команды.  
  
 Примеры см. в разделе [визуализации и моделирования SDK веб-сайт](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
> [!NOTE]
>  Также можно изменить поведение некоторых существующих команд, например "Вырезать", "Вставить", "Выбрать все" и "Печать", переопределив соответствующие методы в CommandSet.cs. Дополнительные сведения см. в разделе [как: изменить стандартную команду меню](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="defining-a-command-using-mef"></a>Определение команды с помощью MEF  
 MEF (Managed Extension Framework) предлагает альтернативный метод определения команд в меню схемы. Его основная задача — включение доменного языка для расширения вами или другими сторонами. Пользователи могут выбрать установить только DSL или DSL и расширения. Кроме того, MEF уменьшает объем работы по определению команд контекстного меню после выполнения начальной работы по включению MEF в DSL.  
  
 Используйте метод, описанный в этом разделе, если:  
  
1.  вы хотите определить команды меню или других меню, кроме контекстного (вызываемого щелчком правой кнопки мыши);  
  
2.  вы хотите настроить определенные группы команд в меню;  
  
3.  вы не хотите разрешать другим пользователям добавлять в DSL их собственные команды;  
  
4.  вы хотите определить только одну команду.  
  
 В остальных случаях используйте для определения команд метод MEF. Дополнительные сведения см. в разделе [расширение доменного языка с помощью MEF](../modeling/extend-your-dsl-by-using-mef.md).  
  
##  <a name="VSCT"></a>Объявите по команде в Commands.Vsct  
 Команды меню объявляются в файле DslPackage\Commands.vsct. Эти определения указывают на метки элементов меню и место их отображения в меню.  
  
 Файл для редактирования, Commands.vsct, импортирует определения из нескольких h-файлы, которые находятся в каталоге *путь установки Visual Studio SDK*\VisualStudioIntegration\Common\Inc. Он также включает файл GeneratedVsct.vsct, который создается из определения DSL.  
  
 Дополнительные сведения о vsct-файлами см. в разделе [Visual Studio Command Table (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
#### <a name="to-add-the-command"></a>Добавление команды  
  
1.  В **обозревателе решений**в разделе **DslPackage** проекта, откройте Commands.vsct.  
  
2.  В элементе `Commands` определите одну или несколько кнопок и группу. Объект *кнопку* элемент меню. Объект *группы* раздел в меню. Чтобы определить эти элементы, добавьте следующий код:  
  
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
    >  Каждая кнопка или группа идентифицируются по GUID и целочисленному идентификатору. Один и тот же GUID можно использовать при создании различных групп и кнопок, но при этом у них должны быть разные идентификаторы. Имена GUID и ID, преобразуются в фактические значения GUID и числовые идентификаторы в `<Symbols>` узла.  
  
3.  Чтобы она загружалась только в контексте вашего доменного языка, добавьте для нее ограничение видимости. Дополнительные сведения см. в разделе [VisibilityConstraints элемент](../extensibility/visibilityconstraints-element.md).  
  
     Для этого добавьте в элемент `CommandTable` после элемента `Commands` следующий код:  
  
    ```  
    <VisibilityConstraints>  
      <!-- Ensures the command is only loaded for this DSL -->  
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"  
        context="guidEditor"/>  
    </VisibilityConstraints>  
    ```  
  
4.  Определите имена, используемые для GUID и идентификаторов. Для этого добавьте `Symbols` в элемент `CommandTable` после элемента `Commands` следующий код:  
  
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
  
5.  Замените `{000...000}` на GUID, идентифицирующий группы и элементы меню. Чтобы получить новый идентификатор GUID, используйте **создать GUID** средство **средства** меню.  
  
    > [!NOTE]
    >  Если вы хотите добавить сразу несколько групп или элементов меню, можно использовать один и тот же GUID. При этом необходимо использовать новые значения для `IDSymbols`.  
  
6.  В скопированном из данной процедуры коде замените собственными строками каждое вхождение следующих строк:  
  
    -   `grpidMyMenuGroup`  
  
    -   `cmdidMyContextMenuCommand`  
  
    -   `guidCustomMenuCmdSet`  
  
    -   `My Context Menu Command`  
  
##  <a name="version"></a>Обновление версии пакета в Package.tt  
 При добавлении или изменении команды обновляйте параметр `version`<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>, который применяется к классу пакета перед выпуском новой версии доменного языка.  
  
 Поскольку класс пакета определяется в созданном классе, обновите атрибут в файле текстового шаблона, из которого создается файл Package.cs.  
  
#### <a name="to-update-the-packagett-file"></a>Обновление файла Package.tt  
  
1.  В **обозревателе решений**в **DslPackage** проекта **GeneratedCode** папку, откройте файл Package.tt.  
  
2.  Найдите элемент `ProvideMenuResource`.  
  
3.  Увеличьте параметр `version` атрибута, который является вторым параметром. При необходимости можно написать имя параметра, прямо указывающее на его назначение. Пример:  
  
     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`  
  
##  <a name="CommandSet"></a>Укажите поведение команды  
 В доменном языке уже имеются некоторые команды, внедренные в разделяемый класс, который был объявлен в файле DslPackage\GeneratedCode\CommandSet.cs. Чтобы добавить новые команды, необходимо расширить этот класс, создав новый файл с частичным объявлением того же класса. Обычно это имя класса  *\<YourDslName >*`CommandSet`. Лучше всего начать с проверки имени класса и его содержимого.  
  
 Класс набора команд производится из <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.  
  
#### <a name="to-extend-the-commandset-class"></a>Расширение класса CommandSet  
  
1.  В Обозревателе решений в проекте DslPackage откройте папку GeneratedCode, найдите раздел CommandSet.tt и откройте созданный в нем файл CommandSet.cs. Запомните пространство имен и имя первого определенного здесь класса. Например:  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  В **DslPackage**, создайте папку с именем **пользовательский код**. В этой папке создайте новый файл класса с именем `CommandSet.cs`.  
  
3.  В новом файле напишите частичное объявление, используя то же пространство имен и имя, что и в созданном частичном классе. Пример:  
  
     `namespace Company.Language1 /* Make sure this is correct */`  
  
     `{ internal partial class Language1CommandSet { ...`  
  
     **Примечание** Если шаблон класса используется для создания нового файла, необходимо исправить пространство имен и имя класса.  
  
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
 Для каждой команды настройте метод `OnStatus...`, определяющий, когда команда будет отображаться в меню и когда она будет включена или затемнена. Задайте свойства `Visible` и `Enabled` `MenuCommand` как показано в следующем примере. Этот метод вызывается для создания контекстного меню каждый раз, когда пользователь щелкает схему правой кнопкой мыши, поэтому должен работать быстро.  
  
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
  
-   `this.CurrentSelection`. Фигура, которую пользователь щелкает правой кнопкой мыши, всегда включается в этот список. Если пользователь щелкает пустую область схемы, схема становится единственным членом списка.  
  
-   `this.IsDiagramSelected()` - `true`Если пользователь щелкнет пустую область схемы.  
  
-   `this.IsCurrentDiagramEmpty()`  
  
-   `this.IsSingleSelection()`-пользователь не выбран нескольких объектов  
  
-   `this.SingleSelection`-Фигура или схема, на который пользователь щелкнул правой кнопкой мыши  
  
-   `shape.ModelElement as MyLanguageElement`-элемент модели, представленной фигуры.  
  
 Как правило, свойство `Visible` должно определяться выбранным параметром, а свойство `Enabled` — состоянием выбранных элементов.  
  
 Метод OnStatus не должен менять состояние Магазина.  
  
### <a name="define-what-the-command-does"></a>Определение действий команды  
 Для каждой команды определите метод `OnMenu...`, выполняющий необходимое действие при выборе этой команды в меню.  
  
 Если изменения вносятся в элементы моделей, необходимо делать это внутри транзакции. Дополнительные сведения см. в разделе [как: изменить стандартную команду меню](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
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
  
 Дополнительные сведения о том, как переходить от одного объекта к объекту в модели, а также о способах создания объектов и ссылок см. в разделе [как: изменить стандартную команду меню](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
### <a name="register-the-command"></a>Регистрация команды  
 Повторите в C# объявления значений GUID и идентификаторов, которые были сделаны в разделе "Символы" CommandSet.vsct:  
  
```  
private Guid guidCustomMenuCmdSet =   
    new Guid("00000000-0000-0000-0000-000000000000");  
private const int grpidMyMenuGroup = 0x01001;  
private const int cmdidMyContextMenuCommand = 1;  
```  
  
 Используйте то же значение GUID, как вставить в **Commands.vsct**.  
  
> [!NOTE]
>  В случае изменений в разделе "Символы" VSCT-файла для сопоставления нужно будет также изменить эти объявления. Кроме того, необходимо увеличить номер версии в Package.tt  
  
 Зарегистрируйте команды меню как часть данного набора команд. `GetMenuCommands()`вызывается один раз после инициализации схеме:  
  
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
  
1.  На **обозревателе решений** инструментов, нажмите кнопку **преобразовать все шаблоны**.  
  
2.  Нажмите клавишу **F5** Перестройте решение и запустить отладку доменного языка в экспериментальную сборку.  
  
3.  В экспериментальном построении откройте пример схемы.  
  
4.  Щелкните несколько элементов в схеме правой кнопкой мыши, чтобы проверить, правильно ли включается и отключается команда, а также правильно ли работает ее отображение или скрытие в зависимости от выбранного элемента.  
  
## <a name="troubleshooting"></a>Устранение неполадок  
 **Команда не отображается в меню:**  
  
-   Пока вы не установите пакет доменного языка, команда будет отображаться только в экземплярах отладки Visual Studio. Дополнительные сведения см. в разделе [развертывание решений доменный язык](../modeling/deploying-domain-specific-language-solutions.md).  
  
-   Убедитесь, что экспериментальный язык имеет правильное расширение имени файла для этого доменного языка. Чтобы проверить расширение имени файла, откройте DslDefinition.dsl в основном экземпляре Visual Studio. Затем в Обозревателе DSL щелкните узел "Редактор" правой кнопкой мыши и выберите "Свойства". В окне "Свойства" проверьте свойство FileExtension.  
  
-   Вы [увеличивать номер версии пакета](#version)?  
  
-   Установите точку останова в начале метода OnStatus. Он должен останавливаться при щелчке правой кнопкой мыши по любой части схемы.  
  
     **Метод OnStatus не вызывается**:  
  
    -   Убедитесь, что GUID и идентификаторы в коде CommandSet совпадают с идентификаторами в разделе "Символы" файла Commands.vsct.  
  
    -   В файле Commands.vsct убедитесь, что GUID и идентификаторы в каждом родительском узле указывают на правильную родительскую группу.  
  
    -   В командной строке Visual Studio введите devenv /rootsuffix exp /setup. Затем перезапустите экземпляр отладки Visual Studio.  
  
-   Выполните метод OnStatus и убедитесь, что command.Visible и command.Enabled имеют значение true.  
  
 **Неправильное меню будет отображаться или команда появляется в том месте**:  
  
-   Убедитесь, что комбинация GUID и идентификатора уникальна для данной команды.  
  
-   Убедитесь, что более ранние версии пакета удалены.  
  
## <a name="see-also"></a>См. также  
 [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Способ: команда меню «Стандартная»](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)   
 [Развертывание решений доменного языка](../modeling/deploying-domain-specific-language-solutions.md)   
 [Пример кода: схемы канала](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
