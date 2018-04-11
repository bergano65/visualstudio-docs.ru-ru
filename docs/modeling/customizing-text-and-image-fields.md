---
title: Настройка текста и полей изображения | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f577669c685d6f42b73c80f947e8edad0c7b9088
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="customizing-text-and-image-fields"></a>Настройка полей с текстом и изображениями
При определении декоратор текста в фигуре, он представлен TextField. Примеры инициализации TextFields и других ShapeFields проверьте Dsl\GeneratedCode\Shapes.cs в решении DSL.  
  
 Текстовое поле — это объект, который управляет область внутри фигуры, такие как пространство, назначенное на метку. Один экземпляр TextField совместно используется много фигур того же класса. Текст подписи отдельно для каждого экземпляра экземпляра TextField не хранит: вместо этого `GetDisplayText(ShapeElement)` метод принимает форму в качестве параметра, а также выполнять поиск текста, зависит от текущего состояния фигуры и его элемент модели.  
  
## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Как определить внешний вид текстового поля  
 `DoPaint()` Метод вызывается для отображения поля на экране. Можно либо переопределить значение по умолчанию `DoPaint(),` или можно переопределить некоторые методы, которые она вызывает. Следующие упрощенную версию по умолчанию методы помогут понять, как переопределить поведение по умолчанию.  
  
```  
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
  
 Существует несколько пар типа `Get` методы и `Default` свойства, такие как `DefaultMultipleLine/GetMultipleLine()`. Можно назначить значение свойству по умолчанию, чтобы изменить значение для всех экземпляров поля формы. Чтобы сделать значение изменяться из одной формы экземпляра на другой или зависит от состояния ее элемента модели или фигуры, переопределите `Get` метод.  
  
## <a name="static-customizations"></a>Статические настроек  
 Если вы хотите изменить каждый экземпляр данного поля формы, сначала узнать ли задание этого свойства в определении DSL. Например можно задать размер шрифта и стиля в окне «Свойства».  
  
 Если нет, затем переопределить `InitializeShapeFields` метод, фигуру класса и присвойте значение на соответствующий `Default...` свойства текстового поля.  
  
> [!WARNING]
>  Для переопределения `InitializeShapeFields()`, необходимо задать **приводит к возникновению ошибки производного типа Double** свойство класса фигуры, чтобы `true` в определении DSL.  
  
 В этом примере фигуры содержит текстовое поле, который будет использоваться для комментариев пользователя. Мы хотим использовать шрифт Стандартная комментарий. Поскольку стандартный шрифт из набора стилей, можно выбрать идентификатор шрифта по умолчанию:  
  
```  
  
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
  
## <a name="dynamic-customizations"></a>Динамические настроек  
 Чтобы изменять внешний вид зависит от состояния фигуры и его элемент модели, являются производными собственный подкласс `TextField` и переопределите один или несколько `Get...` методы. Необходимо также переопределить метод InitializeShapeFields фигуры по и заменить экземпляр TextField экземпляр собственного класса.  
  
 В следующем примере создается шрифт текстового поля, зависит от состояния свойства логического домена фигуры элемента модели.  
  
 Чтобы запустить этот пример кода, создайте новое решение DSL с помощью шаблона минимальной языка. Добавить логическое свойство `AlternateState` в класс ExampleElement домена. Добавьте в класс ExampleShape decorator значок и задать его изображение в файл растрового изображения. Нажмите кнопку **преобразовать все шаблоны**. Добавьте новый файл кода в проекте DSL и вставьте следующий код.  
  
 Чтобы протестировать код, нажмите клавишу F5 и отладки решения, откройте образец диаграммы. Должен появиться значок состояния по умолчанию. Выберите форму и в окне свойств измените значение **AlternateState** свойство. Следует изменить шрифт имя элемента.  
  
```  
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
 В предыдущем примере показано, как можно изменить на любой шрифт, который доступен текстового поля. Однако рекомендуется — измените его на один набор стилей, связанный с фигурой или с приложением. Чтобы сделать это, переопределите <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> или GetTextBrushId().  
  
 Также можно изменить путем переопределения стиля значением фигуры <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Это приводит к изменение шрифтов и кисти для всех полей формы.  
  
## <a name="customizing-image-fields"></a>Настройка полей изображения  
 При определении декоратор изображения в форме, а также при определении изображаемый в форме изображения ImageField управляет область, в котором отображается форма. Примеры инициализации ImageFields и других ShapeFields проверьте Dsl\GeneratedCode\Shapes.cs в решении DSL.  
  
 ImageField — это объект, который управляет область внутри фигуры, такие как пространство, назначенное декоратор. Один экземпляр ImageField совместно используется много фигур того же класса формы. Экземпляр ImageField не хранит отдельный образ для каждой фигуры: вместо этого `GetDisplayImage(ShapeElement)` метод принимает форму в качестве параметра и можно найти изображение, зависит от текущего состояния фигуры и его элемент модели.  
  
 Если требуется специальное поведение, например переменной образ, можно создать свой собственный класс, производный от ImageField.  
  
#### <a name="to-create-a-subclass-of-imagefield"></a>Чтобы создать подкласс ImageField  
  
1.  Задать **приводит к возникновению ошибки производного типа Double** свойства родительского класса фигуры в определение DSL.  
  
2.  Переопределить `InitializeShapeFields` метод класса формы.  
  
    -   Создайте новый файл кода в проекте DSL и записи определение разделяемого класса для класса формы. Переопределите существует определение метода.  
  
3.  Проверьте код элемента `InitializeShapeFields` в DSL\GeneratedCode\Shapes.cs.  
  
     В методе переопределения вызвать базовый метод, а затем создать экземпляр собственного класса поле изображения. Используйте это для замены поля регулярного изображения в `shapeFields` списка.  
  
## <a name="dynamic-icons"></a>Динамические значки  
 Этот пример делает изменить значок зависит от состояния элемента модели фигуры.  
  
> [!WARNING]
>  В этом примере показано, как сделать декоратор динамического изображения. Но если требуется только для переключения от одного или двух изображений в зависимости от состояния модели переменной, проще создать несколько декораторов изображения, их расположении в той же позиции в форму и задайте фильтр видимость, зависящие от конкретных значений модели переменная. Чтобы задать этот фильтр, выберите карта фигур в определения DSL, откройте окно сведений DSL и перейдите на вкладку декораторов.  
  
 Чтобы запустить этот пример кода, создайте новое решение DSL с помощью шаблона минимальной языка. Добавить логическое свойство `AlternateState` в класс ExampleElement домена. Добавьте в класс ExampleShape decorator значок и задать его изображение в файл растрового изображения. Нажмите кнопку **преобразовать все шаблоны**. Добавьте новый файл кода в проекте DSL и вставьте следующий код.  
  
 Чтобы протестировать код, нажмите клавишу F5 и отладки решения, откройте образец диаграммы. Должен появиться значок состояния по умолчанию. Выберите форму и в окне свойств измените значение **AlternateState** свойство. Значок должно отобразиться повернутый до 90 градусов, на этой фигуре.  
  
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
 [Определение фигуры и соединители](../modeling/defining-shapes-and-connectors.md)   
 [Задание фонового изображения для диаграммы](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Навигация по модели и обновление модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)