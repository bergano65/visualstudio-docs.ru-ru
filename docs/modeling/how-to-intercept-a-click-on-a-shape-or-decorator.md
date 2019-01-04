---
title: Как выполнить Перехват щелчка фигуры или декоратора
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: d71cb172929fd9d213c0f09be21c1a844acf4462
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892749"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>Как выполнить Перехват щелчка фигуры или декоратора
Следующие процедуры демонстрируют перехват щелчка фигуры или декоратора значка. Может перехватывать щелчков, производит двойной щелчок, перетаскивает, и другие жесты и сделать элемент отвечать.

## <a name="to-intercept-clicks-on-shapes"></a>Для перехвата щелчков мышью на фигурах
 В проекте Dsl, в файле кода, который отделен от созданных файлах кода напишете определение разделяемого класса для класса shape. Переопределить `OnDoubleClick()` или один из способов, имя которого начинается с `On...`. Пример:

```csharp
public partial class MyShape // change
  {
    public override void OnDoubleClick(DiagramPointEventArgs e)
    {
      base.OnDoubleClick(e);
      System.Windows.Forms.MessageBox.Show("Click");
      e.Handled = true;
  }  }
```

> [!NOTE]
>  Задайте `e.Handled` для `true`, если вам не нужно событие передается содержащего фигуры или схемы.

## <a name="to-intercept-clicks-on-decorators"></a>Для перехвата щелкает декораторов
 Декораторы образа переносятся на экземпляр класса ImageField, который имеет метод OnDoubleClick. Может перехватывать щелчков, при написании подкласса ImageField. Поля определяются в методе InitializeShapeFields. Таким образом необходимо изменить этот метод для создания экземпляра подклассе, а не регулярное ImageField. Метод InitializeShapeFields — в созданном коде класса shape. Можно переопределить класс фигуры, если задать его `Generates Double Derived` свойства, как описано в следующей процедуре.

 Несмотря на то, что InitializeShapeFields является методом экземпляра, он вызывается только один раз для каждого класса. Таким образом существует только один экземпляр ClickableImageField для каждого поля в каждом классе, а не одному экземпляру для каждой фигуры на схеме. При двойном щелчке экземпляра, необходимо определить, какой экземпляр, что достигнута, как показано в примере кода.

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>Для перехвата, щелкнуть значок декоратора

1.  Откройте или создайте решения DSL.

2.  Выберите или создайте фигуры, которая содержит декоратор значок и сопоставление его с доменным классом.

3.  В файле кода отдельно от файлов в `GeneratedCode` папке создайте новый подкласс ImageField:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using System.Collections.Generic;
    using System.Linq;

    namespace Fabrikam.MyDsl { // Change to your namespace
    internal class ClickableImageField : ImageField
    {
      // You can also override OnClick and so on.
      public override void OnDoubleClick(DiagramPointEventArgs e)
      {
        base.OnDoubleClick(e);
        // Work out which instance was hit.
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;
        if (shapeHit != null)
        {
          MyDomainClass element =
              shapeHit.ModelElement as MyDomainClass;
          System.Windows.Forms.MessageBox.Show(
             "Double click on shape for " + element.Name);
          // If we do not set Handled, the event will
          // be passed to the containing shape:
          e.Handled = true;
        }
      }

       public ClickableImageField(string fieldName)
         : base(fieldName)
       { }
    }
    ```

     Необходимо задать обработанных значение true, если требуется отключить события должны быть переданы содержащего фигуры.

4.  Переопределите метод InitializeShapeFields в вашей classs фигуры, добавив следующее определение разделяемого класса.

    ```csharp
    public partial class MyShape // change
    {
     protected override void InitializeShapeFields
          (IList<ShapeField> shapeFields)
     {
      base.InitializeShapeFields(shapeFields);
      // You can see the above method in MyShapeBase
      // in the generated Shapes.cs
      // It has already added fields for the Icons.
      // So you will have to retrieve them and replace with your own.
      ShapeField unwantedField = shapeFields.First
          (field => field.Name == "IconDecorator1");
      shapeFields.Remove(unwantedField);

      // Now replicate the generated code from the base class
      // in Shape.cs, but with your own image constructor.
      ImageField field2 = new ClickableImageField("IconDecorator1");
      field2.DefaultImage = ImageHelper.GetImage(
        MyDslDomainModel.SingletonResourceManager
        .GetObject("MyShapeIconDecorator1DefaultImage"));
          shapeFields.Add(field2);
    }
    ```

1.  Постройте и запустите это решение.

2.  Дважды щелкните значок экземпляра фигуры. Должна появиться тестового сообщения.

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>Перехват щелкает и перетаскивает со списками CompartmentShape
 Следующий пример позволяет пользователю перегруппировывать элементы в фигуру секции, перетаскивая их. Чтобы выполнить этот код:

1. Создание нового решения DSL с помощью **схем классов** шаблона решения.

    Вы также можете работать с собственного решения, содержащего фигуры секций. Предполагается, что имеется отношение внедрения между элементами модели, представленный фигурой и элементов, представленных в списке элементов секции.

2. Задайте **создает двойную производную** свойство фигуры секции.

3. Добавьте следующий код в файле в **Dsl** проекта.

4. Настройте класс и фигуру имена доменов в этот код в соответствии с собственного DSL.

   Таким образом код работает следующим образом. В этом примере `ClassShape` имя фигуры секции.

-   Набор обработчиков событий мыши присоединяется к каждому экземпляру секции при его создании.

-   `ClassShape.MouseDown` Событие сохраняет текущий элемент.

-   При перемещении указателя мыши за пределы текущего элемента, создается экземпляр MouseAction, который задает курсор и захвате мыши до освобождения.

     Чтобы избежать конфликта с другими действиями мыши, таких как текст элемента, выбрав действие MouseAction не создается, пока указатель мыши покинул исходного элемента.

     Альтернативой созданию MouseAction будет просто ожидать MouseUp. Тем не менее это будет работать неправильно, если пользователь отпускает кнопку мыши после перетаскивания его за пределами секции. Действие MouseAction может выполнять соответствующие действия, независимо от того, где кнопка мыши отпущена.

-   Когда указатель мыши отпускается, MouseAction.MouseUp упорядочение порядок ссылок между элементами модели.

-   Изменение порядка роли срабатывает правило, которое обновляет соответствующие элементы. Это поведение уже определен, и дополнительный код не требуется.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships
// displayed in the compartments don't use inheritance
// (don't have base or derived domain relationships).

namespace Company.CompartmentDrag
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements
     .OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item,
  /// but still inside the compartment, create an Action
  /// to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>См. также

- [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)
- [Свойства декораторов](../modeling/properties-of-decorators.md)