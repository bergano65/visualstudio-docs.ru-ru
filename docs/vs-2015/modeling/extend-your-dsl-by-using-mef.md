---
title: Расширение доменного языка с помощью MEF | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e7be79a-53ab-4d79-863a-bef8d27839bd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fd5e4727c4352ca27d905bad608c4a1c17284f9b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930648"
---
# <a name="extend-your-dsl-by-using-mef"></a>Расширение доменного языка с помощью MEF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Доменный язык (DSL) можно расширить с помощью Managed Extensibility Framework (MEF). Вы или другие разработчики смогут создавать расширения для DSL без изменения определения DSL и программного кода. К таким расширениям относятся команды меню, обработчики перетаскивания и вставки и проверки. Пользователи будут иметь возможность установки вашего DSL, а затем при необходимости установить расширения для него.  
  
 Кроме того при включении MEF в DSL, он может быть проще писать некоторые функции вашего DSL, даже если все они создаются вместе с DSL.  
  
 Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Чтобы включить вашего DSL, который необходимо расширить платформой MEF  
  
1. Создайте новую папку с именем **MefExtension** внутри **DslPackage** проекта. К нему, добавьте следующие файлы:  
  
    Имя файла: `CommandExtensionVSCT.tt`  
  
   > [!IMPORTANT]
   >  Задайте идентификатор GUID в этом файле, чтобы совпадал с CommandSetId GUID, который определен в DslPackage\GeneratedCode\Constants.tt  
  
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
  
    Если добавить этот файл, необходимо включить проверки в доменном ЯЗЫКЕ с помощью по крайней мере одного из параметров в **EditorValidation** в обозревателе DSL.  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>  
   ```  
  
    Имя файла: `PackageExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>  
   ```  
  
2. Создайте новую папку с именем **MefExtension** внутри **Dsl** проекта. К нему, добавьте следующие файлы:  
  
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
  
3. Добавьте следующую строку в существующий файл с именем **файле DslPackage\Commands.vsct**:  
  
   ```  
   <Include href="MefExtension\CommandExtensionVSCT.vsct"/>  
   ```  
  
    Вставьте строку после существующего `<Include>` директива.  
  
4. `Open DslDefinition.dsl.`  
  
5. В обозревателе DSL выберите **Editor\Validation**.  
  
6. В окне «Свойства» убедитесь, что по крайней мере одно из свойств с именем **использует...**  является `true`.  
  
7. На панели инструментов обозревателя решений щелкните **преобразовать все шаблоны**.  
  
    Дочерние файлы появляются под каждого из файлов, которые были добавлены.  
  
8. Постройте и запустите решение, чтобы убедиться, что он работает по-прежнему.  
  
   DSL теперь с поддержкой MEF. Команды меню, обработчиков жестов и ограничения проверки можно записывать в виде расширений MEF. Эти расширения можно написать в решение DSL, а также другой пользовательский код. Кроме того, вы или другие разработчики могут создавать отдельные [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширения, расширение доменного языка.  
  
## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>Создание расширения для DSL с поддержкой MEF  
 Если у вас есть доступ к DSL с поддержкой MEF, созданным вами или другим пользователем, можно написать для его расширения. Расширения можно использовать для добавления команды меню, обработчиков жестов или ограничений проверки. Чтобы создать эти расширения, используйте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] решение Extension (VSIX). Решение состоит из двух частей: проект библиотеки классов, который создает сборки кода и проект VSIX, который упаковывает сборки.  
  
#### <a name="to-create-a-dsl-extension-vsix"></a>Для создания DSL расширения VSIX  
  
1. Создайте новый проект библиотеки классов. Для этого в **новый проект** выберите **Visual Basic** или **Visual C#** , а затем выберите **библиотеки классов**.  
  
2. В новый проект библиотеки классов добавьте ссылку на сборку DSL.  
  
   - Эта сборка обычно имеет имя, которое заканчивается на «. DSL.dll».  
  
   - Если у вас есть доступ к проекту DSL, можно найти файл сборки в каталоге **Dsl\bin\\\\***  
  
   - Если у вас есть доступ к DSL VSIX-файлу, вы можете найти сборку, изменив расширение VSIX-файл на «ZIP». Распакуйте ZIP-файл.  
  
3. Добавьте ссылки на следующие сборки .NET:  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll  
  
   -   System.ComponentModel.Composition.dll  
  
   -   System.Windows.Forms.dll  
  
4. Создайте проект VSIX в одном решении. Для этого в **новый проект** диалогового окна последовательно раскройте элементы **Visual Basic** или **Visual C#**, нажмите кнопку **расширяемости**, а затем выберите  **Проект VSIX**.  
  
5. В обозревателе решений щелкните правой кнопкой мыши проект VSIX и нажмите кнопку **Назначить запускаемым проектом**.  
  
6. В новом проекте откройте **source.extension.vsixmanifest**.  
  
7. Нажмите кнопку **добавить содержимое**. В диалоговом окне задайте **тип содержимого** для **компонент MEF**, и **исходный проект** в ваш проект библиотеки классов.  
  
8. Добавьте ссылку VSIX в DSL.  
  
   1. В **source.extension.vsixmanifest**, нажмите кнопку **добавить ссылку**  
  
   2. В диалоговом окне щелкните **полезных данных, добавить** и найдите VSIX-файл DSL. VSIX-файл создается в решение DSL в ** DslPackage\bin\\\\***.  
  
       Это позволяет пользователям устанавливать DSL и расширения, в то же время. Если пользователь уже установил DSL, будет устанавливаться только расширения.  
  
9. Просмотрите и обновите другими полями **source.extension.vsixmanifest**. Нажмите кнопку **выбрать выпуски** и убедитесь, что правильный [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] установлены.  
  
10. Добавьте код в проект библиотеки классов. Используйте примеры в следующем разделе в качестве руководства.  
  
     Можно добавить любое количество команд, жестов и классы проверки.  
  
11. Чтобы проверить расширение, нажмите клавишу **F5**. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]создайте или откройте пример файла класса DSL.  
  
## <a name="writing-mef-extensions-for-dsls"></a>Создание расширений MEF для доменных языков  
 Вы можете написать расширений в проекте кода сборки отдельные расширения решения DSL. Можно также использовать MEF в проекте DslPackage как удобный способ написания команд, жестов и код проверки как часть DSL.  
  
### <a name="menu-commands"></a>Команды меню  
 Для записи команды меню, определите класс, реализующий <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> и префикс класс с атрибутом, который определен в доменном ЯЗЫКЕ, с именем *YourDsl*`CommandExtension`. Вы можете написать более одного класса команды меню.  
  
 `QueryStatus()` вызывается всякий раз, когда пользователь щелкает правой кнопкой мыши схему. Он должен проверить текущее выделение и задать `command.Enabled` чтобы указать, когда применяется команда.  
  
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
 Обработчик жестов умеет работать с объектами при перетаскивании на схему, в любом месте внутри или за пределами [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Следующий пример позволяет пользователю перетаскивать файлы из проводника Windows в схеме. Он создает элементы, которые содержат имена файлов.  
  
 Вы можете написать обработчики для обработки перетаскивания с другими моделями DSL и UML-модели. Дополнительные сведения см. в разделе [как: Добавление обработчика перетаскивания и вставки](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
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
 Методы проверки отмечаются `ValidationExtension` атрибут, который создается по DSL, а также по <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Метод может отображаться в любом классе, который не помечен с помощью атрибута.  
  
 Дополнительные сведения см. в разделе [проверка в доменных языках](../modeling/validation-in-a-domain-specific-language.md).  
  
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
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)   
 [Практическое: Добавление обработчика перетаскивания и вставки](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Проверка в доменных языках](../modeling/validation-in-a-domain-specific-language.md)



