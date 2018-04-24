---
title: Расширение доменного языка с помощью MEF
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a54aca1e3732f366172abc0b4acea92cd28c6fae
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="extend-your-dsl-by-using-mef"></a>Расширение доменного языка с помощью MEF
Доменный язык (DSL) можно расширить с помощью Managed Extensibility Framework (MEF). Вы или другие разработчики смогут для записи расширений для языка DSL без изменения определения DSL и программного кода. К таким расширениям относятся команды меню, обработчиков и перетащите и проверки. Пользователи смогут установить DSL и при необходимости установить расширения для него.

 Кроме того при включении MEF в доменного языка может быть проще писать некоторые возможности DSL, даже если они объединяются вместе с DSL.

 Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Чтобы включить расширение платформой MEF доменного языка

1.  Создайте новую папку с именем **MefExtension** внутри **DslPackage** проекта. Добавьте следующие файлы на него:

     Имя файла: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    >  Идентификатор GUID набора в этот файл должен совпадать с GUID CommandSetId, которая определена в DslPackage\GeneratedCode\Constants.tt

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

     Имя файла: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

     Имя файла: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

     Имя файла: `ValidationExtensionRegistrar.tt`

     При добавлении этого файла, необходимо включить проверки в DSL с помощью по крайней мере один из параметров в **EditorValidation** в обозреватель DSL.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

     Имя файла: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2.  Создайте новую папку с именем **MefExtension** внутри **Dsl** проекта. Добавьте следующие файлы на него:

     Имя файла: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

     Имя файла: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

     Имя файла: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3.  Добавьте следующую строку в существующий файл с именем **DslPackage\Commands.vsct**:

    ```
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

     Вставьте строку после существующего `<Include>` директивы.

4.  `Open DslDefinition.dsl.`

5.  Выберите в обозревателе DSL **Editor\Validation**.

6.  В окне «Свойства» убедитесь, что по крайней мере одно свойство с именем **использует...**  — `true`.

7.  В панели инструментов обозревателя решений щелкните **преобразовать все шаблоны**.

     Дочерние файлы отображаются под каждого из файлов, которые вы добавили.

8.  Постройте и запустите решение, чтобы убедиться, что он по-прежнему работает.

 Теперь DSL поддержкой MEF. В качестве расширений MEF можно написать команды меню, обработчиков жестов и проверочные ограничения. Эти расширения можно написать в решении DSL вместе с другой пользовательский код. Кроме того, вы или другие разработчики можно написать отдельный [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] модулей, расширяющих доменного языка.

## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>Создание расширения для DSL поддержкой MEF
 При наличии доступа к DSL поддержкой MEF, созданные самостоятельно или кто-то другой расширения можно написать для него. Расширения можно использовать для добавления команды меню, обработчиков жестов или проверки ограничений. Чтобы создать эти расширения, используйте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решение Extension (VSIX). Решение состоит из двух частей: проект библиотеки классов, создающий код сборки и проект VSIX, которая упаковывает сборки.

#### <a name="to-create-a-dsl-extension-vsix"></a>Для создания расширения VSIX DSL

1.  Создайте новый проект библиотеки классов. Для этого в **новый проект** выберите **Visual Basic** или **Visual C#** , а затем выберите **библиотеки классов**.

2.  В новый проект библиотеки классов добавьте ссылку на сборку DSL.

    -   Эта сборка обычно имеет имя, которое заканчивается на «. DSL.dll».

    -   Если имеется доступ к проекту DSL, можно найти файл сборки в каталоге **Dsl\bin\\\***

    -   При наличии доступа к DSL VSIX-файл можно найти сборку, изменив расширение VSIX-файл на «ZIP». Распакуйте этот ZIP-файл.

3.  Добавьте ссылки на следующие сборки .NET.

    -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

    -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

    -   System.ComponentModel.Composition.dll

    -   System.Windows.Forms.dll

4.  Создайте проект VSIX в одном решении. Для этого в **новый проект** диалогового окна разверните **Visual Basic** или **Visual C#**, нажмите кнопку **расширяемости**, а затем выберите  **Проект VSIX**.

5.  В обозревателе решений щелкните правой кнопкой мыши проект VSIX и нажмите кнопку **Назначить запускаемым проектом**.

6.  В новом проекте откройте **source.extension.vsixmanifest**.

7.  Нажмите кнопку **Добавление содержимого**. В диалоговом окне задайте **тип содержимого** для **компонент MEF**, и **исходный проект** в ваш проект библиотеки классов.

8.  Добавьте ссылку VSIX DSL.

    1.  В **source.extension.vsixmanifest**, нажмите кнопку **Добавление ссылки**

    2.  В диалоговом окне выберите **добавьте полезных данных** и найдите VSIX-файл DSL. VSIX-файл создается в решении DSL в **DslPackage\bin\\\***.

         Это позволяет пользователям устанавливать языка DSL и расширения, в то же время. Если пользователь уже установил DSL, будет установлен только расширения.

9. Просмотрите и обновите другие поля **source.extension.vsixmanifest**. Нажмите кнопку **выбрать выпуски** и убедитесь, что указана правильная [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] установлены.

10. Добавьте код в проект библиотеки классов. Используйте примеры в следующем разделе в качестве руководства.

     Можно добавить любое количество команд, жестов и классы проверки.

11. Чтобы проверить расширение, нажмите клавиши **F5**. В экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]создайте или откройте файл примере DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Написание расширений MEF для доменного языка
 Расширения можно написать в проекте кода сборки отдельные решения расширения DSL. MEF можно также использовать в проекте DslPackage — удобный способ записи команд, жестов и кода проверки в рамках языка DSL.

### <a name="menu-commands"></a>Команды меню
 Чтобы написать команду меню, определите класс, который реализует <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> и префикса класса с атрибутом, который определен в доменного языка, с именем *YourDsl*`CommandExtension`. Можно написать более одного класса команды меню.

 `QueryStatus()` вызывается каждый раз, когда пользователь щелкает правой кнопкой мыши схему. Его следует проверить текущее выделение и настроить `command.Enabled` для указания того, когда применяется команда.

```
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}

```

### <a name="gesture-handlers"></a>Обработчики жестов
 Обработчик жестов можно обработать объекты при перетаскивании на схему, в любом месте внутри или за пределами [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Следующий пример позволяет пользователю перетаскивать файлы из проводника Windows в схеме. Он создает элементов, содержащих имена файлов.

 Можно написать обработчики для работы с перетаскивания из других DSL моделей и моделей UML. Дополнительные сведения см. в разделе [как: Добавление обработчика и перетащите](../modeling/how-to-add-a-drag-and-drop-handler.md).

```

using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}

```

### <a name="validation-constraints"></a>Ограничения проверки
 Методы проверки помечаются `ValidationExtension` атрибутом, который создан доменный язык, а также по <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Метод может использоваться в любой класс, который не помечен с помощью атрибута.

 Дополнительные сведения см. в разделе [проверка доменного языка](../modeling/validation-in-a-domain-specific-language.md).

```
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }

```

## <a name="see-also"></a>См. также

- [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Практическое руководство. Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Проверка в доменных языках](../modeling/validation-in-a-domain-specific-language.md)