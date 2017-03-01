---
title: "Обновление фигур и соединителей в соответствии с моделью | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 97ec749c0a89dae6c5a98702926d8ad82b6af3ac
ms.lasthandoff: 02/22/2017

---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Обновление фигур и соединителей в соответствии с моделью
В доменном языке в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], чтобы внешний вид фигуры отражают состояние базовой модели.  
  
 В примерах кода в этом разделе должны добавляться к `.cs` файла в вашей `Dsl` проекта. Эти инструкции в каждом файле, необходимо:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Задайте свойства фигуры карты для управления видимостью декоратора  
 Можно управлять видимостью декоратора без написания программного кода, настроив сопоставление фигуры и класс домена в определении DSL. Дополнительные сведения см. в разделе  [способ определения доменного языка](../modeling/how-to-define-a-domain-specific-language.md).
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Предоставляют цвет и стиль фигуры в виде свойств  
 В определении DSL, щелкните правой кнопкой мыши фигуру класса, выберите пункт **добавить предоставленный**и выберите один из элементов, таких как **цвет заливки**.  
  
 Фигура теперь имеет свойство домена, которое можно задать в коде программы или имени пользователя. Например чтобы задать его в программном коде команды или правило, можно написать:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Если вы хотите сделать переменной свойства только под управлением программы, а не пользователем, выберите свойство домена например **цвет заливки** в схеме определения DSL. В окне «Свойства» задайте **возможность просмотра** для `false` или **Readonly пользовательского интерфейса —** для `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Определение правил изменения, чтобы сделать цвет, стиль или расположение зависит от свойства элемента модели  
 Можно определить правила, которые обновят внешний вид фигуры, зависит от других частей модели. Например можно определить изменить правило для элемента модели, который обновляет цвет его фигура, зависит от свойства элемента модели. Дополнительные сведения о правилах изменение в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Правила следует использовать только для обновления свойств, которые хранятся в хранилище, поскольку правила не вызываются при выполнении команды Undo. Это включает некоторые графические функции, такие как размер и видимость фигуры. Для обновления этих компонентов фигуры, в разделе [обновление хранилища не графические функции](#OnAssociatedProperty).  
  
 В следующем примере предполагается, что предоставляется `FillColor` как свойство домена, как описано в предыдущем разделе.  
  
```c#  
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
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Используйте OnChildConfigured для инициализации свойств фигуры  
 Для установки свойств фигуры при первом создании переопределения `OnChildConfigured()` в определении разделяемого класса схемы. Класс схемы, указанный в определении DSL и созданный код находится в **Dsl\Generated Code\Diagram.cs**. Пример:  
  
```c#  
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
  
 Этот метод можно использовать для свойства домена и функции вне хранилища, такие как размер фигуры.  
  
##  <a name="a-nameonassociatedpropertya-use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a>Используйте AssociateValueWith() для обновления других компонентов фигуры  
 Для некоторых функций фигуры, например, имеет ли он тень или стиль стрелки соединительной линии встроенные метода предоставлять функции свойства домена не существует.  Изменения в таких функций не находятся под контролем системы транзакций. Таким образом, не подходит для обновления их с помощью правил, поскольку правила не вызываются, когда пользователь выполняет команду отмены.  
  
 Вместо этого такие функции, можно обновить с помощью <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> В следующем примере стиль стрелки соединительной линии управляется значением свойства домена в отношение, которое отображает соединителя:  
  
```  
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
        { // Update the shape’s built-in Decorator feature:  
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
  
 `AssociateValueWith()`должен быть вызван один раз для каждого свойства домена, который требуется зарегистрировать. После его вызова будет вызывать любые изменения с указанным свойством `OnAssociatedPropertyChanged()` в любой фигуры, представляющие свойства элемента модели.  
  
 Нет необходимости вызывать `AssociateValueWith()` для каждого экземпляра. Несмотря на то, что InitializeResources является методом экземпляра, он вызывается только один раз для каждого класса shape.

