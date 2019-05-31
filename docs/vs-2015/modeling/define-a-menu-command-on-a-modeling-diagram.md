---
title: Определение команды меню на схеме моделирования | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ec230a5bf32ab6e70967e76d31030af3a7a351a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687603"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Определение команды меню на схеме моделирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio можно определить дополнительные пункты контекстных меню схемы UML. Вы можете управлять отображением и доступностью команды в контекстном меню любого элемента на схеме, а также написать код, который запускается при выборе пункта меню пользователем. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) и предоставить их другим пользователям Visual Studio.  

## <a name="requirements"></a>Требования  
 См. раздел [Требования](../modeling/extend-uml-models-and-diagrams.md#Requirements).  

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="defining-the-menu-command"></a>Определение команды меню  
 Чтобы создать команду меню для конструктора UML, необходимо создать класс, определяющий поведение команды, и внедрить этот класс в расширение Visual Studio Integration Extension (VSIX). VSIX выполняет роль контейнера, позволяющего установить команду. Существует два альтернативных способа определения команды меню.  

- **Создание команды меню в ее собственном расширении VSIX с помощью шаблона проекта.** Этот способ быстрее. Используйте его, если не хотите объединять команды меню с другими типами расширения, такими как расширения проверки, пользовательские элементы панели элементов или обработчики жестов.  

- **Создайте отдельную команду меню и проекты VSIX.** Используйте этот метод, если нужно объединить несколько типов расширения в одном расширении VSIX. Например, если для команды меню требуется, чтобы модель соблюдала определенные ограничения, можно внедрить ее в то же расширение VSIX, что и метод проверки.  

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Создание команды меню в ее собственном расширении VSIX  

1. В области **Проекты моделирования** диалогового окна **Новый проект**выберите **Расширение команды**.  

2. Откройте файл **.cs** в новом проекте и измените класс `CommandExtension` для реализации вашей команды.  

    Более подробную информацию см. в разделе [Реализация команды меню](#Implementing).  

3. В этот проект можно добавить дополнительные команды, определив новые классы.  

4. Выполните проверку команды меню, нажав клавишу F5. Более подробную информацию см. в разделе [Выполнение команды меню](#Executing).  

5. Установите команду меню на другой компьютер, скопировав файл **bin\\\*\\\*.vsix** , созданный вашим проектом. Более подробную информацию см. в разделе [Установка и удаление расширения](#Installing).  

   Ниже описана альтернативная процедура.  

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Создание команды меню в отдельном проекте библиотеки классов (DLL)  

1. Создайте проект библиотеки классов либо в новом решении Visual Studio, либо в существующем решении.  

   1. В меню **Файл** последовательно выберите пункты **Создать**и **Проект**.  

   2. В области **Установленные шаблоны**выберите **Visual C#** или **Visual Basic**. В среднем столбце выберите пункт **Библиотека классов**.  

   3. В поле **Решение** укажите, нужно ли создать новое решение или добавить компонент в уже открытое решение VSIX.  

   4. Укажите имя и расположение проекта и нажмите кнопку «ОК».  

2. Добавьте в проект указанные ниже ссылки.  

   |                                                                                                    Ссылка                                                                                                    |                                                                                                  Возможности                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         Определение компонентов с помощью [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        Чтение и изменение свойств элементов модели.                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      Создание элементов модели, изменение фигур на схемах.                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[версия]                                                                                  | Определение обработчиков событий модели.<br /><br /> Инкапсуляция серии изменений в модель. Дополнительные сведения см. в разделе [обновлений модели UML ссылку с помощью транзакций](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[версия]<br /><br /> (требуется не всегда)                                                             |                                                                                   Доступ к дополнительным элементам схемы для обработчиков жестов.                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> Требуется только для команд на схемах слоев. Дополнительные сведения см. в разделе [расширение схем слоев](../modeling/extend-layer-diagrams.md). |                                                                                             Определение команд на схеме слоев.                                                                                              |

3. Добавьте файл класса в проект и вставьте в него указанный ниже код.  

   > [!NOTE]
   > Измените пространство имен, имя класса и значение, возвращаемое `Text` , как вам это необходимо.  
   >   
   >  Если определить несколько команд, они отображаются в меню в алфавитном порядке по именам классов.  

   ```  
   using System.ComponentModel.Composition;     
   using System.Linq;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
   using Microsoft.VisualStudio.Uml.Classes;   
       // ADD other UML namespaces if required  

   namespace UMLmenu1 // CHANGE  
   {  
     // DELETE any of these attributes if the command  
     // should not appear in some types of diagram.  
     [ClassDesignerExtension]  
     [ActivityDesignerExtension]  
     [ComponentDesignerExtension]  
     [SequenceDesignerExtension]  
     [UseCaseDesignerExtension]   
     // [LayerDesignerExtension]  

     // All menu commands must export ICommandExtension:  
     [Export (typeof(ICommandExtension))]  
     // CHANGE class name – determines order of appearance on menu:  
     public class Menu1 : ICommandExtension  
     {  
       [Import]  
       public IDiagramContext DiagramContext { get; set; }  

       public void QueryStatus(IMenuCommand command)  
       { // Set command.Visible or command.Enabled to false  
         // to disable the menu command.  
         command.Visible = command.Enabled = true;  
       }  

       public string Text  
       {  
         get { return "MENU COMMAND LABEL"; }  
       }  

       public void Execute(IMenuCommand command)  
       {  
         // A selection of starting points:  
         IDiagram diagram = this.DiagramContext.CurrentDiagram;  
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
         { IElement element = shape.Element; }  
         IModelStore modelStore = diagram.ModelStore;  
         IModel model = modelStore.Root;  
         foreach (IElement element in modelStore.AllInstances<IClass>())   
         { }  
       }  
     }  
   }  
   ```  

    Более подробную информацию о том, что следует помещать в методы, см. в разделе [Реализация команды меню](#Implementing).  

   Команду меню необходимо добавить в проект VSIX, который выступает контейнером для установки команды. При необходимости в проект VSIX можно добавить и другие компоненты.  

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Добавление команды меню в проект VSIX  

1. Эта процедура не требуется, если команда меню создана со своим собственным расширением VSIX.  

2. Создайте проект VSIX, если ваше решение еще его не содержит.  

    1. В контекстном меню решения в **обозревателе решений**выберите пункт **Добавить**, а затем **Новый проект**.  

    2. В разделе **Установленные шаблоны**разверните узел **Visual C#** или **Visual Basic**и выберите пункт **Расширение среды**. В среднем столбце выберите пункт **Проект VSIX**.  

3. В контекстном меню проекта VSIX в обозревателе решений выберите пункт **Назначить запускаемым проектом**.  

4. Откройте **source.extension.vsixmanifest**.  

    1. На вкладке **Метаданные** введите имя для VSIX.  

    2. На вкладке **Цели установки** задайте в качестве целевых объектов версии Visual Studio.  

    3. На вкладке **Активы** выберите **Создать**и укажите в диалоговом окне следующие значения:  

         **Тип** = **Компонент MEF**  

         **Источник** = **Проект в текущем решении**  

         **Проект** = *Ваш проект библиотеки классов*  

## <a name="Implementing"></a> Реализация команды меню  
 Класс команды меню реализует необходимые методы для <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>.  

|||  
|-|-|  
|`string Text { get; }`|Возвратите метку пункта меню.|  
|`void QueryStatus(IMenuCommand command);`|Вызывается, когда пользователь щелкает схему правой кнопкой мыши.<br /><br /> Этот метод не должен изменять модель.<br /><br /> Используйте `DiagramContext.CurrentDiagram.SelectedShapes` , чтобы определить, должна ли команда отображаться и быть доступной.<br /><br /> Задайте следующие значения:<br /><br /> -   `command.Visible` Чтобы `true` Если команда должна отображаться в меню, когда пользователь щелкает правой кнопкой мыши в диаграмме<br />-   `command.Enabled` Чтобы `true` Если пользователь может щелкнуть команду в меню<br />-   `command.Text` Чтобы задать метку меню в динамическом режиме|  
|`void Execute (IMenuCommand command);`|Вызывается при выборе пункта меню пользователем, если этот пункт отображается и доступен.|  

### <a name="accessing-the-model-in-code"></a>Доступ к модели в коде  
 Включение следующего объявления в класс команды меню:  

```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  

 ...  

 Объявление `IDiagramContext` позволяет создавать код в методах, осуществляющих доступ к схеме, текущему выделению и модели:  

```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}  
```  

### <a name="navigating-and-updating-the-model"></a>Перемещение по модели и ее обновление  
 Все элементы модели UML доступны через API. Из текущего выбранного элемента или из корня модели можно получить доступ ко всем другим элементам. Дополнительные сведения см. в разделе [Навигация по UML-модели](../modeling/navigate-the-uml-model.md) и [программирование с UML API](../modeling/programming-with-the-uml-api.md).  

 Если вы имеете дело со схемой последовательностей, см. также [изменение последовательностей UML с помощью UML API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  

 API также позволяет изменять свойства элементов, удалять элементы и отношения и создавать новые элементы и отношения.  

 По умолчанию каждое изменение, вносимое в метод Execute, будет выполняться в отдельной транзакции. Пользователь сможет отменить каждое изменение по отдельности. Если вы хотите объединить изменения в одной транзакции, используйте <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> как описано в разделе [обновлений модели UML ссылку с помощью транзакций](../modeling/link-uml-model-updates-by-using-transactions.md).  

### <a name="use-the-ui-thread-for-updates"></a>Использование потока пользовательского интерфейса для обновлений  
 В некоторых случаях может оказаться полезным выполнять обновления модели из фонового потока. Например, если команда загружает данные из медленного ресурса, можно выполнить загрузку в фоновом потоке, чтобы пользователь мог видеть вносимые изменения и при необходимости отменить операцию.  

 Однако следует помнить, что хранилище моделей не является потокобезопасным. Следует всегда использовать поток пользовательского интерфейса для выполнения обновления и, если это возможно, запретить пользователям вносить изменения во время выполнения фоновой операции. Например, см. в разделе [обновление модели UML из фонового потока](../modeling/update-a-uml-model-from-a-background-thread.md).  

## <a name="Executing"></a> Выполнение команды меню  
 В целях проверки запустите команду в режиме отладки.  

#### <a name="to-test-the-menu-command"></a>Проверка команды меню  

1. Нажмите клавишу **F5**или выберите команду **Начать отладку** в меню **Отладка**.  

     Запустится экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  

     **Устранение неполадок**: Если новый [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не запускается:  

    - При наличии нескольких проектов убедитесь в том, что для проекта VSIX задан параметр "Назначить запускаемым проектом".  

    - В обозревателе решений в контекстном меню запускаемого или единственного проекта выберите пункт **Свойства**. В редакторе свойств проекта перейдите на вкладку **Отладка** . Убедитесь в том, что строка в поле **Запуск внешней программы** является полным путем к [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]; обычно она имеет следующий вид:  

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  

2. В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]откройте или создайте проект моделирования и откройте или создайте схему моделирования. Используйте схему, которая относится к одному из типов, перечисленных в атрибутах вашего класса команды меню.  

3. Откройте контекстное меню в любом месте схемы. Команда должна появиться в меню.  

     **Устранение неполадок**: Если команда не отображается в меню, убедитесь, что:  

    - Проект команды меню указан в качестве компонента MEF на вкладке **Активы** в **source.extensions.manifest** проекта VSIX.  

    - Параметры атрибутов `Import` и `Export` являются допустимыми.  

    - `QueryStatus` Не задает метод `command`.`Enabled` или `Visible` значение `false`.  

    - Используемый тип схемы модели (класс UML, последовательность и т. п.) указан как один из атрибутов класса команды меню `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` и т. д.  

## <a name="Installing"></a> Установка и удаление расширения  
 Расширение [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] можно установить как на своем компьютере, так и на других.  

#### <a name="to-install-an-extension"></a>Установка расширения  

1. На компьютере найдите файл **.vsix** , который был создан проектом VSIX.  

    1. В контекстном меню проекта VSIX в **обозревателе решений**выберите пункт **Открыть папку в проводнике Windows**.  

    2. Найдите файл **bin\\\*\\** _Ваш_проект_ **.vsix**  

2. Скопируйте файл **.vsix** на компьютер, где необходимо установить расширение. Это может быть как ваш собственный компьютер, так и любой другой.  

     На конечном компьютере должен быть установлен один из выпусков [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , заданный в **source.extension.vsixmanifest**.  

3. На конечном компьютере откройте файл **.vsix** , например дважды щелкнув его.  

     Откроется**установщик расширений Visual Studio** , который устанавливает расширение.  

4. Запустите или перезапустите [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  

#### <a name="to-uninstall-an-extension"></a>Удаление расширения  

1. В меню **Сервис** щелкните пункт **Расширения и обновления**.  

2. Разверните узел **Установленные расширения**.  

3. Выберите расширение и щелкните **Удалить**.  

   Иногда неисправное расширение не удается загрузить, в результате чего в окне ошибок создается отчет, который не отображается в диспетчере расширений. В этом случае расширение можно удалить, удалив файл из следующей папки:  

   *% LocalAppData %* **\Local\Microsoft\VisualStudio\\\Extensions [версия]**  

## <a name="MenuExample"></a> Пример  
 В приведенном ниже примере показан код для команды меню, позволяющий поменять местами имена двух элементов на схеме классов. Этот код должен быть встроен в проект расширения [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и установлен в соответствии с описанием в предыдущих разделах.  

```  
using System.Collections.Generic; // for IEnumerable  
using System.ComponentModel.Composition;  
  // for [Import], [Export]  
using System.Linq; // for IEnumerable extensions  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
  // for IDiagramContext  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
  // for designer extension attributes  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  // for ShapeElement  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext  
using Microsoft.VisualStudio.Uml.Classes;  
  // for class diagrams, packages  

/// <summary>  
/// Extension to swap names of classes in a class diagram.  
/// </summary>  
namespace SwapClassNames  
{  
  // Declare the class as an MEF component:  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  // Add more ExportMetadata attributes to make  
  // the command appear on diagrams of other types.  
  public class NameSwapper : ICommandExtension  
  {  
  // MEF required interfaces:  
  [Import]  
  public IDiagramContext Context { get; set; }  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  

  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  /// <param name="command"></param>  
  public void Execute(IMenuCommand command)  
  {  
    // Get selected shapes that are IClassifiers -  
    // IClasses, IInterfaces, IEnumerators.  
    var selectedShapes = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  

    // Get model elements displayed by shapes.  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  

    // Do the swap in a transaction so that user  
    // cannot undo one change without the other.  
    using (ILinkedUndoTransaction transaction =  
    LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
    string firstName = firstElement.Name;  
    firstElement.Name = lastElement.Name;  
    lastElement.Name = firstName;  
    transaction.Commit();  
    }  
  }  

  /// <summary>  
  /// Called by Visual Studio to determine whether  
  /// menu item should be visible and enabled.  
  /// </summary>  
  public void QueryStatus(IMenuCommand command)  
  {   
    int selectedClassifiers = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>().Count();  
    command.Visible = selectedClassifiers > 0;  
    command.Enabled = selectedClassifiers == 2;  
  }  

  /// <summary>  
  /// Name of the menu command.  
  /// </summary>  
  public string Text  
  {  
    get { return "Swap Names"; }  
  }  
  }  

}  
```  

## <a name="see-also"></a>См. также  
 [Определение и Установка расширения моделирования](../modeling/define-and-install-a-modeling-extension.md)   
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Определение обработчика жестов на схеме моделирования](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Определение настраиваемого элемента панели элементов моделирования](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Определение ограничений проверки для моделей UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Редактирование схем последовательностей UML с помощью UML API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)   
 [Программирование с UML API](../modeling/programming-with-the-uml-api.md)   
 [Пример. Команда для выравнивания фигур на схеме UML](http://go.microsoft.com/fwlink/?LinkID=213809)
