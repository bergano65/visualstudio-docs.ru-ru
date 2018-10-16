---
title: Добавление команд и жестов в схемы слоев | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, adding custom commands
- layer diagrams, adding custom gestures
ms.assetid: ac9c417b-0b40-4a90-86f5-ee3cbdce030b
caps.latest.revision: 40
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3985372ba8c6aa8ba198f70a3538e3062a6d89ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223224"
---
# <a name="add-commands-and-gestures-to-layer-diagrams"></a>Добавление команд и жестов в схемы слоев
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете определить команды контекстного меню и обработчики жестов на схемах слоев в Visual Studio. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension (VSIX) и предоставить их другим пользователям Visual Studio.  
  
 Если нужно, можно определить несколько команд и обработчиков жестов в том же проекте Visual Studio. Можно также объединить несколько проектов в одно расширение VSIX. Например, можно определить одно расширение VSIX, включающее в себя команды слоя, доменный язык и команды для схем UML.  
  
> [!NOTE]
>  Можно также настроить проверку архитектуры, в которой исходный код пользователей сравнивается со схемами слоев. Проверку архитектуры следует определять в отдельном проекте Visual Studio. Его можно добавить в то же расширение VSIX, что и другие расширения. Дополнительные сведения см. в разделе [Добавление пользовательской проверки архитектуры в схемы слоев](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
## <a name="requirements"></a>Требования  
 См. раздел [Требования](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Определение команды или жеста в новом расширении VSIX  
 Самый быстрый способ создания расширения заключается в использовании шаблона проекта. Он помещает код и манифест VSIX в один проект.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Определение расширения с использованием шаблона проекта  
  
1.  Создайте проект в новом решении, выбрав команду **Создать проект** в меню **Файл** .  
  
2.  В области **Проекты моделирования** диалогового окна **Новый проект**выберите **Расширение команд конструктора слоев** или **Расширение жестов конструктора слоев**.  
  
     Шаблон создает проект, который содержит небольшой рабочий пример.  
  
3.  Чтобы проверить расширение, нажмите клавиши **CTRL+F5** или **F5**.  
  
     Запустится экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . В этом экземпляре создайте схему слоев. Расширение команды или жеста должно работать в этой схеме.  
  
4.  Закройте экспериментальный экземпляр и измените пример кода. Дополнительные сведения см. в разделе [Navigate и обновления уровня модели в программном коде](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
5.  В тот же самый проект можно добавить дополнительные команды или обработчики жестов. Более подробную информацию см. в одном из следующих разделов:  
  
     [Определение команды меню](#command)  
  
     [Определение обработчика жестов](#gesture)  
  
6.  Чтобы установить расширение в основном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]или на другом компьютере, найдите файл **.vsix** в **bin\\\***. Скопируйте его на компьютер, а затем дважды щелкните его. Чтобы удалить расширение, выберите пункт **Расширения и обновления** в меню **Сервис** .  
  
## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Добавление команды или жеста в отдельное расширение VSIX  
 Если нужно создать один файл VSIX, который содержит проверяющие элементы слоев, команды и другие расширения, рекомендуется создать один проект для определения VSIX и отдельные проекты для обработчиков. Сведения о других типах расширения моделирования см. в разделе [моделей и схем UML, расширение](../modeling/extend-uml-models-and-diagrams.md).  
  
#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Добавление расширений слоев в отдельный файл VSIX  
  
1.  Создайте проект библиотеки классов в новом или существующем решении Visual Studio. В диалоговом окне **Новый проект** щелкните **Visual C#** и выберите **Библиотека классов**. Этот проект будет содержать классы команд или обработчиков жестов.  
  
    > [!NOTE]
    >  В одной библиотеке классов можно определить более одного класса команд или обработчиков жестов, однако классы проверки слоев следует определять в отдельной библиотеке классов.  
  
2.  Определите или создайте проект VSIX в решении. Проект VSIX содержит файл с именем **source.extension.vsixmanifest**. Чтобы добавить проект VSIX, выполните указанные ниже действия.  
  
    1.  В диалоговом окне **Новый проект** разверните узел **Visual C#**, выберите **Расширение среды**, а затем щелкните **Проект VSIX**.  
  
    2.  В обозревателе решений щелкните правой кнопкой мыши проект VSIX и выберите пункт **Назначить запускаемым проектом**.  
  
    3.  Щелкните **Выбрать выпуски** и убедитесь в том, что установлен флажок **Visual Studio** .  
  
3.  В **source.extension.vsixmanifest**в разделе **Активы**добавьте проект команды или обработчика жестов в качестве компонента MEF.  
  
    1.  На вкладке **Активы**выберите команду **Создать**.  
  
    2.  В поле **Тип**выберите **Microsoft.VisualStudio.MefComponent**.  
  
    3.  В поле **Источник**выберите **Проект в текущем решении** и выберите имя проекта команды или обработчика жестов.  
  
    4.  Сохраните файл.  
  
4.  Вернитесь в проект команды или обработчика жестов и добавьте указанные ниже ссылки на проект.  
  
|**Ссылка**|**Возможности**|  
|-------------------|------------------------------------|  
|Program Files\Microsoft Visual Studio [версия]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Создание и редактирование слоев|  
|Microsoft.VisualStudio.Uml.Interfaces|Создание и редактирование слоев|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Изменение фигур на схемах|  
|System.ComponentModel.Composition|Определение компонентов с помощью Managed Extensibility Framework (MEF)|  
|Microsoft.VisualStudio.Modeling.Sdk.[версия]|Определение расширений моделирования|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[версия]|Обновление фигур и схем|  
  
1.  Измените файл класса в проекте библиотеки классов C# таким образом, чтобы он содержал код вашего расширения. Более подробную информацию см. в одном из следующих разделов:  
  
     [Определение команды меню](#command)  
  
     [Определение обработчика жестов](#gesture)  
  
     См. также [Navigate и обновления уровня модели в программном коде](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
2.  Чтобы проверить функцию, нажмите клавиши CTRL+F5 или F5. Открывается экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. В этом экземпляре создайте или откройте схему слоев.  
  
3.  Чтобы установить расширение в основной экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]или на другом компьютере, найдите файл **.vsix** в каталоге **bin** проекта VSIX. Скопируйте его на компьютер, где требуется выполнить установку VSIX. Дважды щелкните файл VSIX в проводнике Windows (или проводнике в Windows 8).  
  
     Чтобы удалить расширение, выберите пункт **Расширения и обновления** в меню **Сервис** .  
  
##  <a name="command"></a> Определение команды меню  
 В существующий проект жестов или команд можно добавить дополнительные определения команд меню. Каждая команда определяется классом, имеющим указанные ниже характеристики.  
  
-   Класс объявляется следующим образом:  
  
     `[LayerDesignerExtension]`  
  
     `[Export(typeof(ICommandExtension))]`  
  
     `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`  
  
-   Пространство имен и имя класса не имеют значения.  
  
-   Методы, реализующие `ICommandExtension` , указаны ниже.  
  
    -   `string Text {get;}` — метка, которая отображается в меню.  
  
    -   `void QueryStatus(IMenuCommand command)` — вызывается, когда пользователь щелкает схему правой кнопкой мыши и определяет, должна ли команда отображаться и быть доступна для выбранного пользователем элемента.  
  
    -   `void Execute(IMenuCommand command)` — вызывается, когда пользователь выбирает команду.  
  
-   Для определения текущего выделенного элемента можно импортировать `IDiagramContext`:  
  
     `[Import]`  
  
     `public IDiagramContext DiagramContext { get; set; }`  
  
     `...`  
  
     `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`  
  
 Дополнительные сведения см. в разделе [Navigate и обновления уровня модели в программном коде](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
 Чтобы добавить новую команду, создайте файл кода, содержащий приведенный ниже пример. После этого измените и протестируйте его.  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
  
namespace MyLayerExtension // Change to your preference.  
{  
  // This is a feature for Layer diagrams:  
  [LayerDesignerExtension]  
  // This feature is a menu command:  
  [Export(typeof(ICommandExtension))]  
  // Change the class name to your preference:  
  public class MyLayerCommand : ICommandExtension  
  {  
    [Import]  
    public IDiagramContext DiagramContext { get; set; }  
  
    [Import]  
    public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
    // Menu command label:  
    public string Text  
    {  
      get { return "Duplicate layers"; }  
    }  
  
    // Called when the user right-clicks the diagram.  
    // Defines whether the command is visible and enabled.  
    public void QueryStatus(IMenuCommand command)  
    {   
      command.Visible =   
      command.Enabled = DiagramContext.CurrentDiagram  
        .SelectedShapes.Count() > 0;  
    }  
  
    // Called when the user selects the command.  
    public void Execute(IMenuCommand command)  
    {  
      // A selection of starting points:  
      IDiagram diagram = this.DiagramContext.CurrentDiagram;  
      ILayerModel lmodel = diagram.GetLayerModel();  
      foreach (ILayer layer in lmodel.Layers)  
      { // All layers in model.  
      }  
      // Updates should be performed in a transaction:  
      using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("copy selection"))  
      {  
        foreach (ILayer layer in   
          diagram.SelectedShapes  
            .Select(shape=>shape.GetLayerElement())  
            .Where(element => element is ILayer))  
        {  
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");  
          // Position the shapes:  
          IShape originalShape = layer.GetShape();  
          copy.GetShape().Move(  
            originalShape.XPosition + originalShape.Width * 1.2,  
            originalShape.YPosition);  
        }  
        t.Commit();  
      }  
    }  
  }  
}  
```  
  
##  <a name="gesture"></a> Определение обработчика жестов  
 При перетаскивании элементов на схему слоев и при двойном щелчке в любом месте на схеме отвечает обработчиков жестов.  
  
 В существующий проект VSIX команды или обработчика жестов можно добавить файл кода, определяющий обработчик жестов:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
namespace MyLayerExtensions // change to your preference  
{  
  [LayerDesignerExtension]  
  [Export(typeof(IGestureExtension))]  
  public class MyLayerGestureHandler : IGestureExtension  
  {  
  }  
}  
```  
  
 Об обработчиках свойств необходимо помнить следующее.  
  
-   Члены `IGestureExtension` показаны ниже:  
  
     **OnDoubleClick** — вызывается при двойном щелчке в любом месте на схеме.  
  
     **CanDragDrop** — вызывается несколько раз в том случае, когда пользователь перемещает указатель мыши на схему при перетаскивании элемента. Должен работать быстро.  
  
     **OnDragDrop** — вызывается, когда пользователь перетаскивает элемент на схему.  
  
-   Первым аргументом каждого метода является `IShape`, из которого можно получить элемент слоя. Например:  
  
    ```  
    public void OnDragDrop(IShape target, IDataObject data)  
    {  
        ILayerElement element = target.GetLayerElement();  
        if (element is ILayer)  
        {  
            // ...  
        }  
    }  
    ```  
  
-   Обработчики для некоторых типов перетаскиваемых элементов уже определены. Например, пользователь может перетаскивать элементы из обозревателя решений на схему слоев. Для этих типов элементов нельзя определить обработчик перетаскивания. В этих случаях ваши методы `DragDrop` не вызываются.  
  
 Дополнительные сведения о декодировании других элементов при перетаскивании на схему см. в разделе [определение обработчика жестов на схеме моделирования](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="see-also"></a>См. также  
 [Перейдите и обновлять модели слоя в программном коде](../modeling/navigate-and-update-layer-models-in-program-code.md)   
 [Добавление пользовательской проверки архитектуры в схемы слоев](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Определение и установка расширения моделирования](../modeling/define-and-install-a-modeling-extension.md)



