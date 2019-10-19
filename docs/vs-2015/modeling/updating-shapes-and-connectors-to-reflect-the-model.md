---
title: Обновление фигур и соединителей для отражения модели | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c31d54a87ff305504496eac6ae02900334c0966a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659445"
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Обновление фигур и соединителей в соответствии с моделью
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В предметно-ориентированном языке в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно сделать так, чтобы внешний вид фигуры отражал состояние базовой модели.

 Примеры кода в этом разделе следует добавить в файл `.cs` в проекте `Dsl`. Эти инструкции понадобятся в каждом файле:

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Настройка свойств карт фигур для управления видимостью декоратора
 Можно управлять видимостью декоратора без написания программного кода, настроив сопоставление между фигурой и классом домена в определении DSL. Дополнительные сведения см. в следующих разделах:

- [Практическое руководство. Управление видимостью декоратора — перенаправление](../misc/how-to-control-the-visibility-of-a-decorator-redirect.md)

- [Определение доменного языка](../modeling/how-to-define-a-domain-specific-language.md)

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Предоставить цвет и стиль фигуры как свойства
 В определении DSL щелкните правой кнопкой мыши класс Shape, наведите указатель на пункт **добавить предоставленный**и выберите один из таких элементов, как **Цвет заливки**.

 Теперь фигура имеет свойство предметной области, которое можно задать в программном коде или в качестве пользователя. Например, чтобы задать его в программном коде команды или правила, можно написать:

 `shape.FillColor = System.Drawing.Color.Red;`

 Если нужно сделать переменную свойства только под управлением программы, а не пользователем, выберите новое свойство домена, такое как **Цвет заливки** на схеме определения DSL. Затем в окно свойств задайте для параметра режим **просмотра значение `false`** или задано значение `true` для **интерфейса ReadOnly** .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Определение правил изменения для создания цвета, стиля или расположения зависит от свойств элемента модели
 Можно определить правила, которые обновляют внешний вид фигуры, зависят от других частей модели. Например, можно определить правило изменения для элемента модели, который обновляет цвет его фигуры в зависимости от свойств элемента модели. Дополнительные сведения о правилах изменения см. в разделе [правила распространяют изменения в модели](../modeling/rules-propagate-changes-within-the-model.md).

 Правила следует использовать только для обновления свойств, которые хранятся в хранилище, так как правила не вызываются при выполнении команды undo. Сюда не входят некоторые графические функции, такие как размер и видимость фигуры. Сведения об обновлении этих функций фигуры см. в разделе [обновление графических функций, не связанных с хранением](#OnAssociatedProperty).

 В следующем примере предполагается, что вы предоставляли `FillColor` как свойство домена, как описано в предыдущем разделе.

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

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Использование Ончилдконфигуред для инициализации свойств фигуры
 Чтобы задать свойства фигуры при ее первоначальном создании, переопределение `OnChildConfigured()` в частичном определении класса схемы. Класс схемы указан в определении DSL, а созданный код — в **Дсл\женератед коде\диаграм.КС**. Пример:

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

 Этот метод можно использовать как для свойств домена, так и для функций, не связанных с хранилищем, таких как размер фигуры.

## <a name="OnAssociatedProperty"></a>Использование АссоЦиатевалуевис () для обновления других функций фигуры
 Для некоторых функций фигуры, например, имеет ли она тень или стиль стрелки соединителя, встроенный метод предоставления этой функции в качестве свойства предметной области отсутствует.  Изменения таких функций не управляются системой транзакций. Таким образом, не рекомендуется обновлять их с помощью правил, так как правила не вызываются, когда пользователь выполняет команду «Отменить».

 Вместо этого можно обновить такие функции с помощью <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. В следующем примере стиль стрелки для соединителя управляется значением свойства домена в связи, отображаемой соединителем.

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

 `AssociateValueWith()` должны вызываться один раз для каждого свойства домена, которое необходимо зарегистрировать. После вызова все изменения указанного свойства будут вызывать `OnAssociatedPropertyChanged()` в любой фигуре, представляющей элемент модели свойства.

 Нет необходимости вызывать `AssociateValueWith()` для каждого экземпляра. Хотя Инитиализересаурцес является методом экземпляра, он вызывается только один раз для каждого класса Shape.
