---
title: Обновление фигур и соединителей в соответствии с моделью
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e436999b16a89f4956f0fef48a8878a7f609d1f9
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860047"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Изменение фигур и соединителей в соответствии с моделью

В доменный язык в Visual Studio можно сделать внешний вид фигуры отражать состояние объекта базовой модели.

В примерах кода в этом разделе должны добавляться к `.cs` файлов в вашей `Dsl` проекта. Необходимо, чтобы эти инструкции в каждом файле:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Установить свойства карты фигур, чтобы управлять видимостью декоратора

Можно управлять видимостью декоратора без написания программного кода, настроив сопоставление между фигурой и доменный класс в определении DSL. Дополнительные сведения см. в разделе [способ определения доменного языка](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Предоставляют цвет и стиль фигуры в виде свойств

В определении DSL щелкните класс фигуры правой кнопкой мыши **добавить предоставленный**и выберите один из элементов, таких как **цвет заливки**.

Фигура теперь имеет свойство домена, которое можно задать в программном коде или имени пользователя. Например чтобы задать его в программном коде команды или правило, можно написать:

`shape.FillColor = System.Drawing.Color.Red;`

Если вы хотите сделать переменную свойства только под управлением программы, а не пользователем, выберите свойство домена например **цвет заливки** в схеме определения DSL. В окне «Свойства» задайте **возможность просмотра** для `false` или задать **является пользовательский Интерфейс только для чтения** для `true`.

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Определить правила изменения, чтобы сделать цвет, стиль или расположение зависят от свойств элемента модели
 Можно определить правила, которые обновляют внешний вид фигуры, зависят от других частей модели. Например можно определить правила изменения на элемент модели, которая обновляет цвет его фигуры, зависит от свойства элемента модели. Дополнительные сведения о правилах изменений см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).

 Правила следует использовать только для того, чтобы обновить свойства, которые поддерживаются в Store, так как правила, не вызываются при выполнении команды Undo. Сюда не входят некоторые графические функции, такие как размер и видимость фигуры. Чтобы обновить эти функции фигуры, см. в разделе [обновление Non-Store графические функции](#OnAssociatedProperty).

 В следующем примере предполагается, что вы предоставили `FillColor` как свойство домена, как описано в предыдущем разделе.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }

```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Использовать OnChildConfigured для инициализации свойства фигуры

Чтобы задать свойства фигуры, сразу после создания переопределения `OnChildConfigured()` в частичном определении класса схемы. Класс схемы, указанный в определении DSL, а созданный код находится в **Dsl\Generated Code\Diagram.cs**. Пример:

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}

```

Этот метод может использоваться как для свойства домена и функции вне хранилища, такие как размер фигуры.

## <a name="OnAssociatedProperty"></a> Используйте AssociateValueWith(), чтобы обновить некоторые свойства фигуры

Для некоторых функций фигуры, например имеет ли она тень или стиль стрелки соединительной линии отсутствует встроенный метод раскрытия компонента, как свойство домена.  Изменения в такие функции, не находятся под контролем системы транзакций. Таким образом, не подходит для их обновления с помощью правил, так как правила, не вызываются, когда пользователь выполняет команду отмены.

Вместо этого можно обновить с помощью таких функций <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. В следующем примере значение свойства домена в отношение, которое отображает соединитель управляется стиль стрелки соединительной линии:

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` должен вызываться один раз для каждого свойства домена, который вы хотите зарегистрировать. После его вызова, любые изменения к указанному свойству будет вызывать `OnAssociatedPropertyChanged()` в любые фигуры, которые представляют свойства элемента модели.

Нет необходимости вызывать `AssociateValueWith()` для каждого экземпляра. Несмотря на то, что InitializeResources является методом экземпляра, он вызывается только один раз для каждого класса фигуры.
