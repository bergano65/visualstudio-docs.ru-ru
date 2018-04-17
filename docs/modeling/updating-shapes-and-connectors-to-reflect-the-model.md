---
title: Обновление фигур и соединителей в соответствии с моделью | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4c1db67cfa07afeb5427e540163ae37312a2c625
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Обновление фигур и соединителей в соответствии с моделью
В доменного языка в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], чтобы внешний вид фигуры отражают состояние базовой модели.  
  
 В примерах кода в этом разделе, которые должны быть добавлены в `.cs` файла в вашей `Dsl` проекта. Эти инструкции в каждом файле потребуется:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Задать свойства карты фигур для управления видимостью декоратор  
 Можно управлять видимостью декоратор без написания программного кода, настроив сопоставление фигуры и класс домена в определения DSL. Дополнительные сведения см. в разделе [способ определения доменного языка](../modeling/how-to-define-a-domain-specific-language.md).
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Предоставляют цвет и стиль фигуры в виде свойств  
 Определение DSL, щелкните правой кнопкой мыши фигуру класса, выберите пункт **добавьте предоставляется**и выберите один из элементов, таких как **цвет заливки**.  
  
 Фигура теперь имеет свойства домена, который можно задать в коде программы или имени пользователя. Например чтобы задать его в коде программы, команды или правило, можно написать:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Если вы хотите сделать переменной свойства только в программе управления версиями, а не пользователем, выберите новое свойство домена например **цвет заливки** в схема определения DSL. В окне «Свойства» установите **является отображаемым** для `false` или задать **Readonly пользовательского интерфейса —** для `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Определить правила изменения, чтобы сделать цвет, стиль или расположение зависит от свойств элементов модели  
 Можно определить правила, которые обновляют внешний вид фигуры, зависящее от других частей модели. Например можно определить изменить правило для элемента модели, который обновляет цвет его фигуры, зависит от свойства элемента модели. Дополнительные сведения о правилах изменений см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Правила следует использовать только для обновления свойств, которые хранятся в хранилище, потому что правила не вызываются, когда выполняется команда Undo. Это не относится к некоторых графических возможностей, таких как размер и видимость фигуры. Чтобы обновить эти компоненты фигуры, см. [обновление хранилища не графические функции](#OnAssociatedProperty).  
  
 В следующем примере предполагается, что вы предоставили `FillColor` как свойства домена, как описано в предыдущем разделе.  
  
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
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Используйте OnChildConfigured для инициализации свойств фигуры  
 Задание свойств фигуры сразу после создания переопределения `OnChildConfigured()` в определении разделяемого класса схемы. Класс схемы, указанный в определении DSL и созданный код находится в **Dsl\Generated Code\Diagram.cs**. Пример:  
  
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
  
 Этот метод можно использовать для свойства домена и не хранилище функции, такие как размер фигуры.  
  
##  <a name="OnAssociatedProperty"></a> Использовать для обновления других компонентов фигуры associatevaluewith)  
 Для некоторых функций фигуры, например, имеет ли тень или стиль стрелки соединительной линии отсутствует метод встроенных раскрытия компонента, как свойства домена.  Изменения таких компонентов, не под управлением системы транзакции. Таким образом, не подходит для их обновления с помощью правил, поскольку правила не вызываются, когда пользователь выполняет команду отмены.  
  
 Вместо этого можно обновить с помощью таких компонентов, <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. В следующем примере значение свойства домена в отношение, которое отображает соединитель управляется стиль стрелки соединительной линии:  
  
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
  
 `AssociateValueWith()` должен быть вызван один раз для каждого свойства домена, который требуется зарегистрировать. После его вызова, все изменения к указанному свойству будет вызывать `OnAssociatedPropertyChanged()` в фигуры, представляющие свойства элемента модели.  
  
 Нет необходимости вызывать `AssociateValueWith()` для каждого экземпляра. Несмотря на то, что InitializeResources является методом экземпляра, он вызывается только один раз для каждого класса формы.
