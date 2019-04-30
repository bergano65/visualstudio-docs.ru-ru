---
title: Отображение модели UML на схемах | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 694b4dd1531dc196d06ba46eb8c5b77f66052bc2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436230"
---
# <a name="display-a-uml-model-on-diagrams"></a>Отображение модели UML на схемах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В программном коде для расширения Visual Studio можно управлять отображением элементов модели на схемах. Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
В этом разделе.  
- [Отображение элемента на схеме](#Display)  
  
- [Доступ к фигурам, представляющим элемент](#GetShapes)  
  
- [Перемещение и изменение размера фигуры](#Moving)  
  
- [Удаление фигуры со схемы](#Removing)  
  
- [Открытие и создание схем](#Opening)  
  
- [Пример: Команда для выравнивания фигур](#AlignCommand)  
  
## <a name="Display"></a> Отображение элемента на схеме  
 При создании элемента, такого как вариант использования или действие, пользователь может видеть его в обозревателе моделей UML, однако он не всегда автоматически отображается на схеме. В некоторых случаях для его отображения необходимо написать код. В следующей таблице приведены сводные сведения о доступных альтернативах.  
  
|Тип элемента|Пример|Чтобы отобразить это, ваш код должен соответствовать следующим требованиям|  
|---------------------|-----------------|-------------------------------------|  
|Классификатор|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Создайте связанные фигуры на заданных схемах. Можно создать любое количество фигур для каждого классификатора.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Задайте для `parentShape` значение `null` для фигуры на верхнем уровне схемы.<br /><br /> Отображение одной фигуры внутри другой:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);` **Примечание:**  Если вы выполняете отображение Display внутри **ILinkedUndo** транзакций, иногда метод не возвращает `IShape`. Однако фигура создается правильно и доступна посредством `IElement.Shapes().`|  
|Дочерний элемент классификатора|Атрибут, операция,<br /><br /> Часть, порт|Выполняется автоматически — код не требуется.<br /><br /> Он отображается в качестве части родительского элемента.|  
|Поведение|Взаимодействие (последовательность),<br /><br /> Действие|Привяжите поведение к соответствующей схеме.<br /><br /> Каждое поведение одновременно можно привязать только к одной.<br /><br /> Пример:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|  
|Дочерний элемент поведения|Жизненные циклы, сообщения, действия, узлы объектов|Выполняется автоматически — код не требуется.<br /><br /> Отображается, если родительский объект привязан к схеме.|  
|Relationship|Ассоциация, обобщение, поток, зависимость|Выполняется автоматически — код не требуется.<br /><br /> Он отображается на каждой схеме, на которой показаны оба конца.|  
  
## <a name="GetShapes"></a> Доступ к фигурам, представляющим элемент  
 Фигура, представляющая элемент, принадлежит к следующим типам:  
  
 `IShape`  
  
 `IShape<` *ElementType* `>`  
  
 где *ElementType* — это тип элемента модели, такие как `IClass` или `IUseCase`.  
  
|||  
|-|-|  
|`anElement.Shapes ()`|Все объекты `IShapes`, представляющие этот элемент в открытых схемах.|  
|`anElement.Shapes(aDiagram)`|Все объекты `IShapes`, представляющие этот элемент в определенной схеме.|  
|`anIShape.GetElement()`|Объект `IElement`, который представляет фигура. Обычно он приводится к классу IElement.|  
|`anIShape.Diagram`|Объект `IDiagram`, содержащий фигуру.|  
|`anIShape.ParentShape`|Фигура, содержащая `anIShape`. Например, фигура порта содержится внутри фигуры компонента.|  
|`anIShape.ChildShapes`|Фигуры, содержащиеся в `IShape` или `IDiagram`.|  
|`anIShape.GetChildShapes<IUseCase>()`|Фигуры, содержащиеся в `IShape` или `IDiagram`, которые представляют элементы указанного типа, такого как `IUseCase`.|  
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Приведите универсальный `IShape` к строго типизированному `IShape<IElement>`.|  
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Приведите фигуру из одного параметризованного типа фигуры в другой.|  
  
## <a name="Moving"></a> Перемещение и изменение размера фигуры  
  
|||  
|-|-|  
|`anIShape.Move(x, y, [width], [height])`|Переместите фигуру или измените ее размер.|  
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Активируйте окно и прокрутите схему, чтобы все заданные фигуры были видны. Все фигуры должны находиться на схеме. Если `zoomToFit` имеет значение true, схема будет при необходимости масштабироваться, чтобы обеспечить отображение всех фигур.|  
  
 Например, см. в разделе [определение команды выравнивания](#AlignCommand).  
  
## <a name="Removing"></a> Удаление фигуры со схемы  
 Фигуры некоторых типов элементов можно удалить без удаления самого элемента.  
  
|Элемент модели|Удаление фигуры|  
|-------------------|-------------------------|  
|Классификатор: класс, интерфейс, перечисление, субъект, вариант использования или компонент|`shape.Delete();`|  
|Поведение: взаимодействие или действие|Можно удалить схему из проекта. Используйте `IDiagram.FileName` для получения пути.<br /><br /> Это не приводит к удалению поведения из модели.|  
|Любая другая фигура|вы не можете явно удалить другие фигуры со схемы. Фигура автоматически исчезнет, если элемент удаляется из модели или если родительская фигура удаляется со схемы.|  
  
## <a name="Opening"></a> Открытие и создание схем  
  
### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Доступ к текущей схеме пользователя из расширения команды или жеста  
 Объявите это импортированное свойство в своем классе:  
  
 `[Import]`  
  
 `IDiagramContext Context { get; set; }`  
  
 В методе осуществите доступ к схеме:  
  
 `IClassDiagram classDiagram =`  
  
 `Context.CurrentDiagram as IClassDiagram;`  
  
> [!NOTE]
> Экземпляр `IDiagram` (и его подтипы, такие как `IClassDiagram`) является действительным только в рамках обрабатываемой команды. Не рекомендуется сохранять объект `IDiagram` в переменной, которая сохраняется при возвращении управления пользователю.  
  
 Дополнительные сведения см. в разделе [определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="to-obtain-a-list-of-open-diagrams"></a>Получение списка открытых схем  
 Список схем, открытых в проекте в настоящий момент:  
  
```  
Context.CurrentDiagram.ModelStore.Diagrams()  
```  
  
## <a name="to-access-the-diagrams-in-a-project"></a>Доступ к схемам в проекте.  
 API [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно использовать для открытия и создания схем и проектов моделирования.  
  
 Обратите внимание на приведение из `EnvDTE.ProjectItem` к `IDiagramContext`.  
  
```  
  
      using EnvDTE; // Visual Studio API  
...  
[Import]  
public IServiceProvider ServiceProvider { get; set; }  
...  
// Get Visual Studio API  
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;  
// Get current Visual Studio project  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
// Open and process every diagram in the project.  
foreach (ProjectItem item in project.ProjectItems)  
{  
  // Cast ProjectItem to IDiagramContext  
  IDiagramContext context = item as IDiagramContext;  
  if (context == null)  
  {  
     // This is not a diagram file.  
     continue;  
  }  
  // Open the file and give the window the focus.  
  if (!item.IsOpen)  
  {  
      item.Open().Activate();  
  }  
  // Get the diagram.  
  IDiagram diagram = context.CurrentDiagram;  
  // Deal with specific diagram types.  
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;  
  if (seqDiagram != null)  
  { ... } } }  
```  
  
 Экземпляры `IDiagram` и его подтипы не являются действительными после возвращения управления в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Также можно получить в хранилище моделей из проекта [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
```  
  
      Project project = ...;  
IModelStore modelStore = (project as IModelingProject).Store;  
```  
  
## <a name="AlignCommand"></a> Пример: Команда для выравнивания фигур  
 Следующий код реализует команду меню, аккуратно выравнивающую фигуры. Пользователю следует сначала расположить две или более фигур, приблизительно выровняв их по вертикали или по горизонтали. Затем можно использовать команду выравнивания для выравнивания их центров.  
  
 Чтобы сделать команду доступной, добавьте этот код в проект команд меню, а затем разверните полученное расширение для пользователей. Дополнительные сведения см. в разделе [определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace AlignCommand  
{  
  // Implements a command to align shapes in a UML class diagram.  
  // The user first selects shapes that are roughly aligned either vertically or horizontally.  
  // This command will straighten them up.  
  
  // Place this file in a menu command extension project.  
  // See http://msdn.microsoft.com/library/ee329481.aspx  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension] // TODO: Add other diagram types if needed  
  class CommandExtension : ICommandExtension  
  {  
    /// <summary>  
    /// See http://msdn.microsoft.com/library/ee329481.aspx  
    /// </summary>  
    [Import]  
    IDiagramContext context { get; set; }  
  
    /// <summary>  
    /// Transaction context.  
    /// See http://msdn.microsoft.com/library/ee330926.aspx  
    /// </summary>  
    [Import]  
    ILinkedUndoContext linkedUndo { get; set; }  
  
    /// <summary>  
    /// Called when the user selects the command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      Align(context.CurrentDiagram.SelectedShapes);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks on the diagram.  
    /// Determines whether the command is enabled.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;  
      // Make it visible if there are shapes selected:  
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);  
  
      // Make it enabled if there are two or more shapes that are roughly in line:  
      command.Enabled = currentSelection.Count() > 1  
        && (HorizontalAlignCenter(currentSelection) > 0.0  
        || VerticalAlignCenter(currentSelection) > 0.0);  
  
    }  
  
    /// <summary>  
    /// Title of the menu command.  
    /// </summary>  
    public string Text  
    {  
      get { return "Align Shapes"; }  
    }  
  
    /// <summary>  
    /// Find a horizontal line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double Y = -1.0;  
      double top = 0.0, bottom = shapes.First().Bottom();  
      foreach (IShape shape in shapes)  
      {  
        top = Math.Max(top, shape.Top());  
        bottom = Math.Min(bottom, shape.Bottom());  
      }  
      if (bottom > top) Y = (bottom + top) / 2.0;  
      return Y;  
    }  
  
    /// <summary>  
    /// Find a vertical line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double X = -1.0;  
      double left = 0.0, right = shapes.First().Right();  
      foreach (IShape shape in shapes)  
      {  
        left = Math.Max(left, shape.Left());  
        right = Math.Min(right, shape.Right());  
      }  
      if (right > left) X = (right + left) / 2.0;  
      return X;  
    }  
  
    /// <summary>  
    /// Line up those shapes that are roughly aligned.  
    /// </summary>  
    /// <param name="shapes"></param>  
    private void Align(IEnumerable<IShape> shapes)  
    {  
      if (shapes.Count() > 1)  
      {  
        // The shapes must all overlap either horizontally or vertically.  
        // Find a horizontal line that is covered by all the shapes:  
        double Y = HorizontalAlignCenter(shapes);  
        if (Y > 0.0) // Negative if they don't overlap.  
        {  
          // Adjust all the shape positions in one transaction:  
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
          {  
            foreach (IShape shape in shapes)  
            {  
              shape.AlignYCenter(Y);  
            }  
            t.Commit();  
          }  
        }  
        else  
        {  
          // Find a vertical line that is covered by all the shapes:  
          double X = VerticalAlignCenter(shapes);  
          if (X > 0.0) // Negative if they don't overlap.  
          {  
            // Adjust all the shape positions in one transaction:  
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
            {  
              foreach (IShape shape in shapes)  
              {  
                shape.AlignXCenter(X);  
              }  
              t.Commit();  
            }  
          }  
        }  
      }  
    }  
  }  
  
  /// <summary>  
  /// Convenience extensions for IShape.  
  /// </summary>  
  public static class IShapeExtension  
  {  
    public static double Bottom(this IShape shape)  
    {  
      return shape.YPosition + shape.Height;  
    }  
  
    public static double Top(this IShape shape)  
    {  
      return shape.YPosition;  
    }  
  
    public static double Left(this IShape shape)  
    {  
      return shape.XPosition;  
    }  
  
    public static double Right(this IShape shape)  
    {  
      return shape.XPosition + shape.Width;  
    }  
  
    public static void AlignYCenter(this IShape shape, double Y)  
    {  
      shape.Move(shape.XPosition, Y - shape.YCenter());  
    }  
  
    public static void AlignXCenter(this IShape shape, double X)  
    {  
      shape.Move(X - shape.XCenter(), shape.YPosition);  
    }  
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double YCenter(this IShape shape)  
    {  
        return shape.Height / 2.0;  
    }   
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double XCenter(this IShape shape)  
    {  
        return shape.Width / 2.0;  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>См. также  
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Навигация по модели UML](../modeling/navigate-the-uml-model.md)   
 [Пример. Выравнивание фигур на схеме команды меню](http://go.microsoft.com/fwlink/?LinkId=213809)   
 [Пример. Создание элементов, фигур и стереотипов](http://go.microsoft.com/fwlink/?LinkId=213811)
