---
title: Настройка полей с текстом и изображениями
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d14dd126806e2c7b9a903e415dbc7a8a6f834517
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566899"
---
# <a name="customizing-text-and-image-fields"></a>Настройка полей с текстом и изображениями
При определении текстовый декоратор фигуры, он представлен TextField. Примеры инициализацию TextFields и других которым ShapeFields проверьте Dsl\GeneratedCode\Shapes.cs в решение DSL.

 TextField — это объект, который управляет область внутри фигуры, такие как пространство, назначенное метку. Один экземпляр TextField совместно используется много фигур того же класса. Текст подписи отдельно для каждого экземпляра экземпляра TextField не хранит: вместо этого `GetDisplayText(ShapeElement)` метод принимает форму в качестве параметра, а также выполнять поиск текста, зависит от текущего состояния фигуры и его элемента модели.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Как определяется внешний вид текстового поля
 `DoPaint()` Метод называется отображаются на экране. Можно либо переопределить значение по умолчанию `DoPaint(),` или можно переопределить некоторые методы, которые он вызывает. Следующие упрощенную версию по умолчанию методы помогут вам понять, как переопределить поведение по умолчанию:

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }

```

 Существует несколько пар типа `Get` методы и `Default` свойства, такие как `DefaultMultipleLine/GetMultipleLine()`. Значение можно назначить свойство по умолчанию, чтобы изменить значение для всех экземпляров поля фигуры. Чтобы задать более высокое значение отличаться от экземпляра одной формы в другую или зависит от состояния фигуры или его элемента модели, переопределите `Get` метод.

## <a name="static-customizations"></a>Статические настроек
 Если вы хотите изменить каждое вхождение данное поле фигуры, сначала Узнайте указывает, можно задать свойства в определении DSL. Например можно задать размер шрифта и стиля в окне «Свойства».

 Если это не так, затем переопределить `InitializeShapeFields` метод фигуру класса и присвоить ей значение соответствующего `Default...` свойства текстового поля.

> [!WARNING]
>  Чтобы переопределить `InitializeShapeFields()`, необходимо задать **создает двойную производную** свойство класса фигуры, чтобы `true` в определении DSL.

 В этом примере фигуры содержит текстовое поле, который будет использоваться для комментариев пользователя. Мы хотим использовать шрифт стандартным. Так как стандартные шрифт из набор стилей, можно задать идентификатор шрифта по умолчанию:

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;

```

## <a name="dynamic-customizations"></a>Динамические настройки
 Чтобы сделать внешний различаются, зависит от состояния фигуры и его элемента модели, являются производными собственный подкласс `TextField` и переопределите один или несколько `Get...` методы. Необходимо также переопределить метод InitializeShapeFields вашей фигуры и заменить экземпляр TextField экземпляр своего класса.

 В следующем примере создается шрифт текстового поля, зависит от состояния свойства логического домена элемента модели фигуры.

 Чтобы запустить этот пример кода, создайте новое решение DSL с помощью шаблона минимальный язык. Добавить логическое свойство `AlternateState` ExampleElement классом домена. Добавьте в класс ExampleShape декоратор значок и задать его изображение в файл растрового изображения. Нажмите кнопку **преобразовать все шаблоны**. Добавьте новый файл кода в проекте DSL и вставьте следующий код.

 Чтобы протестировать код, нажмите клавишу F5 и, в решение для отладки, откройте пример схемы. Состояние по умолчанию значок должна появиться. Выберите фигуру и в окне «Свойства» измените значение **AlternateState** свойство. Следует изменить шрифт имя элемента.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }

```

## <a name="style-sets"></a>Задает стиль
 В предыдущем примере показано, как текстовое поле можно изменить на любой шрифт, который доступен. Тем не менее более предпочтительно, как изменить его на один из набор стилей, связанный с фигурой или с приложением. Чтобы сделать это, переопределите <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> или GetTextBrushId().

 Также можно изменить набор стилей фигуры путем переопределения <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Это влияет изменение шрифтов и кисти для всех полей фигуры.

## <a name="customizing-image-fields"></a>Настройка полей изображения
 При определении декоратор изображения фигуры, а также при определении фигуру изображения, области, в котором отображается фигуры управляется ImageField. Примеры инициализацию ImageFields и других которым ShapeFields проверьте Dsl\GeneratedCode\Shapes.cs в решение DSL.

 ImageField — это объект, который управляет область внутри фигуры, такие как пространство, назначенное декоратор. Один экземпляр ImageField совместно используется много фигур того же класса фигуры. Экземпляр ImageField не хранит отдельный образ для каждой фигуры: вместо этого `GetDisplayImage(ShapeElement)` метод принимает форму как параметр и выполнять поиск изображений, зависит от текущего состояния фигуры и его элемента модели.

 Если требуется специальное поведение, например переменной изображение, можно создать свой собственный класс, производный от ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Чтобы создать подкласс ImageField

1.  Задайте **создает двойную производную** свойства родительского класса фигуры в определении DSL.

2.  Переопределить `InitializeShapeFields` метод класса фигуры.

    -   Создайте новый файл кода в проекте DSL и написать определение разделяемого класса для класса shape. Переопределите метод существует.

3.  Проверьте код элемента `InitializeShapeFields` в DSL\GeneratedCode\Shapes.cs.

     В методе переопределения вызвать базовый метод и затем создать экземпляр собственного класса поля изображения. Используется для поменяйте местами поля стандартным в `shapeFields` списка.

## <a name="dynamic-icons"></a>Динамические значки
 В этом примере позволяет изменить значок зависит от состояния элемента модели фигуры.

> [!WARNING]
>  В этом примере показано, как осуществлять декоратор динамического изображения. Но если требуется только для переключения между один или два образа в зависимости от состояния переменной модели, проще создать несколько декораторов образ, найдите их в той же позиции на фигуре и установите фильтр видимости, чтобы он зависел от определенных значений модели переменная. Чтобы задать этот фильтр, выберите сопоставление фигуры в определении DSL, откройте окно сведений DSL и перейдите на вкладку декораторов.

 Чтобы запустить этот пример кода, создайте новое решение DSL с помощью шаблона минимальный язык. Добавить логическое свойство `AlternateState` ExampleElement классом домена. Добавьте в класс ExampleShape декоратор значок и задать его изображение в файл растрового изображения. Нажмите кнопку **преобразовать все шаблоны**. Добавьте новый файл кода в проекте DSL и вставьте следующий код.

 Чтобы протестировать код, нажмите клавишу F5 и, в решение для отладки, откройте пример схемы. Состояние по умолчанию значок должна появиться. Выберите фигуру и в окне «Свойства» измените значение **AlternateState** свойство. Значок должно отобразиться повернутый через 90 градусов, на этой фигуре.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}

```

## <a name="see-also"></a>См. также

- [Определение фигур и соединителей](../modeling/defining-shapes-and-connectors.md)
- [Задание фонового изображения схемы](../modeling/setting-a-background-image-on-a-diagram.md)
- [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)