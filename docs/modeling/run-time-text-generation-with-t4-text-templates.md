---
title: Создание текста во время выполнения с помощью текстовых шаблонов T4 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 30956435c321a45a3a1ee32a305080d35b073293
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Создание текста во время выполнения с помощью текстовых шаблонов T4

Текстовые строки в приложении во время выполнения можно создавать с помощью текстовых шаблонов времени выполнения Visual Studio. Чтобы в Visual Studio нет компьютера, на котором выполняется приложение. Шаблоны времени выполнения иногда называются «обработанных текстовых шаблонов», так как во время компиляции, шаблон создает код, который выполняется во время выполнения.

Каждый шаблон представляет собой сочетание текста, которое будет отображаться в создаваемую строку и фрагменты программного кода. Программные фрагменты предоставляют значения для переменных частей строки и управляют условными и повторяющимися частями.

Например следующий шаблон может использоваться в приложении, которое создает отчет в формате HTML.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Обратите внимание, что шаблон HTML-страницу, в которой переменные части были заменены программного кода. Конструктора такой страницы можно начать с написания статического прототипа HTML-страницы. Затем может заменить таблицу и другие переменные части программным кодом, который формирует содержимое, которое отличается от случая к следующему.

С помощью шаблона в приложении проще увидеть окончательную форму выходных данных, чем, например, длинной последовательности инструкций записи. Внесение изменений в форму выходных данных становится проще и надежнее.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Создание шаблона текста во время выполнения в любом приложении

### <a name="to-create-a-run-time-text-template"></a>Чтобы создать шаблон текста во время выполнения

1. В обозревателе решений в контекстном меню проекта, выберите **добавить**, **новый элемент**.

2. В **Добавление нового элемента** выберите **текстовый шаблон времени выполнения**. (В Visual Basic найдите **общих элементов** > **Общие**.)

3. Введите имя для файла шаблона.

    > [!NOTE]
    > Имя файла шаблона будет использоваться как имя класса в созданном коде. Таким образом он не должен иметь пробелы или знаки препинания.

4. Выберите **Добавить**.

    Создан новый файл с расширением **.tt**. Его **пользовательский инструмент** свойству **TextTemplatingFilePreprocessor**. Он содержит следующие строки:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Преобразование существующего файла в шаблон времени выполнения

Для преобразования существующего пример выходных данных является удобным способом создания шаблона. Например если приложение будет создавать HTML-файлы, можно запустить, создав обычный HTML-файл. Убедитесь, что оно правильно работает и правильность его внешний вид. Затем включите его в проект Visual Studio и преобразовать его в шаблон.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Для преобразования существующего текстового файла в шаблон времени выполнения

1. Включите файл в проект Visual Studio. В обозревателе решений в контекстном меню проекта выберите **добавить** > **существующий элемент**.

2. Присвойте свойству файла **средства пользовательских** свойства **TextTemplatingFilePreprocessor**. В обозревателе решений в контекстном меню файла, выберите **свойства**.

    > [!NOTE]
    > Если свойство уже задано, убедитесь в том, что это **TextTemplatingFilePreprocessor** и не **TextTemplatingFileGenerator**. Это может произойти, если вы включили файл, уже имеет расширение **.tt**.

3. Измените расширение имени файла на **.tt**. Несмотря на то, что этот шаг является необязательным, он помогает избежать открыть этот файл в том редакторе.

4. Удалите все пробелы или знаки пунктуации из основной части имени файла. Например «My Web Page.tt» будет неверным, но «MyWebPage.tt» указано правильно. Имя файла будет использоваться как имя класса в созданном коде.

5. Вставьте следующую строку в начало файла. Если вы работаете в проекте Visual Basic, замените «C#» на «VB».

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Содержимое шаблона во время выполнения

### <a name="template-directive"></a>Директивы шаблона

Сохраните первую строку шаблона, в котором он был при создании файла:

`<#@ template language="C#" #>`

Параметр language будет зависеть от языка проекта.

### <a name="plain-content"></a>Чистое содержимое

Изменить **.tt** файл, содержащий текст, который требуется для создания приложения. Пример:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Внедренный программный код

Программный код между можно вставлять `<#` и `#>`. Пример:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Обратите внимание, что инструкции вставляются между `<# ... #>` и выражения вставляются между `<#= ... #>`. Дополнительные сведения см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Использование шаблона

### <a name="the-code-built-from-the-template"></a>Код, построенный на основе шаблона

При сохранении **.tt** файл дочерняя компания **.cs** или **.vb** создается файл. Чтобы просмотреть этот файл в обозревателе решений, разверните **.tt** узел файла. В проекте Visual Basic, сначала выберите **Показать все файлы** в панели инструментов обозревателя решений.

Обратите внимание, что дочерний файл содержит разделяемый класс, который содержит метод с именем `TransformText()`. Этот метод можно вызывать из приложения.

### <a name="generating-text-at-run-time"></a>Создание текста во время выполнения

В коде приложения можно создать это содержимое шаблона с помощью вызова следующим образом:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Чтобы поместить создаваемого класса в конкретном пространстве имен, задайте **Custom Tool Namespace** свойство файла текстового шаблона.

### <a name="debugging-runtime-text-templates"></a>Отладка среды выполнения текстовые шаблоны

Отладка и тестирование текстовые шаблоны времени выполнения в так же, как обычный код.

В текстовом шаблоне можно установить точку останова. При запуске приложения в режиме отладки из Visual Studio, можно пошагово проходить по коду и вычисления выражений Контрольное значение обычным образом.

### <a name="passing-parameters-in-the-constructor"></a>Передача параметров в конструкторе

Обычно шаблон должен импортировать некоторые данные из других частей приложения. Чтобы облегчить эту задачу, код создается с помощью шаблона — это разделяемый класс. Можно создать другую часть этого же класса в другой файл проекта. Этот файл может содержать конструктор с параметрами, свойства и функции, доступные как для кода, внедренного в шаблон, так и с остальной части приложения.

Например, можно создать отдельный файл **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

В файле шаблона **MyWebPage.tt**, можно написать:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Чтобы использовать этот шаблон в приложении:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Параметры конструктора в Visual Basic

В Visual Basic используется отдельный файл **MyWebPageCode.vb** содержит:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Файл шаблона может содержать:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Шаблон может быть вызван с помощью передачи параметра в конструкторе:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Передача данных в свойствах шаблона

Добавление открытых свойств в класс шаблона в определении разделяемого класса — альтернативный способ передачи данных в шаблон. Приложение может задать свойства перед вызовом `TransformText()`.

Кроме того, можно добавить поля в определении разделяемого класса шаблона. Это дает возможность передачи данных между последовательными выполнениями шаблона.

### <a name="use-partial-classes-for-code"></a>Использование разделяемых классов для кода

Многие разработчики предпочитают избежать написания больших фрагментов кода в шаблонах. Вместо этого можно задать методы в разделяемом классе с тем же именем, что файл шаблона. Вызовите эти методы из шаблона. Таким образом показано в шаблоне более четко строки выходных данных целевого будет выглядеть. Обсуждения внешнего результата можно отделить от логики создания данных, которые отображаются.

### <a name="assemblies-and-references"></a>Сборки и ссылки

Если требуется, чтобы код шаблона для ссылки .NET или другую сборку, таких как **System.Xml.dll**, добавьте его в проект **ссылки** обычным образом.

Если вы хотите импортировать пространство имен в так же, как `using` инструкции, это можно сделать с помощью `import` директиву:

```
<#@ import namespace="System.Xml" #>
```

Эти директивы должны размещаться в начале файла, сразу после `<#@template` директивы.

### <a name="shared-content"></a>Общее содержимое

Если у вас есть текст, который будет использоваться в нескольких шаблонах, можно разместить его в отдельном файле и включить его в каждый файл, в которых должен отображаться:

```
<#@include file="CommonHeader.txt" #>
```

Включенное содержимое может содержать любое сочетание программного кода и обычный текст и другие директивы включения и другие директивы.

Директива включения можно использовать в любом месте в тексте файла шаблона или включенного файла.

### <a name="inheritance-between-run-time-text-templates"></a>Наследование между текстовыми шаблонами времени выполнения

Можно настроить обмен содержимым между шаблонами времени выполнения путем написания шаблон базового класса, который может быть абстрактным. Используйте `inherits` параметр `<@#template#>` директивы ссылок на другой класс шаблона среды выполнения.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Шаблон наследования: фрагменты в базовых методах

В шаблоне, используемом в примере ниже Обратите внимание на следующее:

- Базовый класс `SharedFragments` определяет методы в блоки возможностей класса `<#+ ... #>`.

- Базовый класс не содержит свободных текст. Вместо этого все его текстовые блоки встречаются внутри методов функций класса.

- Производный класс вызывает методы, определенные в `SharedFragments`.

- Приложение вызывает `TextTransform()` метод производного класса, но не преобразует базовый класс `SharedFragments`.

- Базовый и производный классы являются текстовые шаблоны времени выполнения; то есть **пользовательский инструмент** свойству **TextTemplatingFilePreprocessor**.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Полученные выходные данные:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Шаблон наследования: Текст в основной части базового

В этот альтернативный подход к использованию наследования шаблонов большая часть текста определяется в базовый шаблон. Производные шаблон предоставляют данных и фрагменты текста, которое помещается в базовое содержимое.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Код приложения:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Полученные выходные данные:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>См. также

Шаблоны времени разработки: Если вы хотите использовать шаблон для создания кода, становится частью вашего приложения см. в разделе [создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Шаблоны времени выполнения может использоваться в любом приложении, где шаблонов и их содержимое определяются во время компиляции. Но если вы планируете написать расширение Visual Studio, создающий текст из шаблонов, которые изменяются во время выполнения, см. [вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>См. также

- [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md)
- [Написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md)
- [Панель элементов T4](http://olegsych.com/T4Toolbox/)