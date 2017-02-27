---
title: "Run-Time Text Generation with T4 Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Preprocessed Text Template project item"
  - "TextTemplatingFilePreprocessor custom tool"
  - "text templates, TransformText() method"
  - "text templates, generating files at run time"
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 22
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 22
---
# Run-Time Text Generation with T4 Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно создавать текстовые строки в приложении во время выполнения с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] текстовые шаблоны во время выполнения.  На компьютере, на котором выполняется приложение, не обязательно должна быть установлена система [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Шаблоны во время выполнения, иногда называются «предварительная обработка текстовых шаблонов», так как во время компиляции шаблона формирует код, выполняемый во время выполнения.  
  
 Каждый шаблон представляет собой сочетание текста в том виде, в каком он будет представлен в сгенерированной строке, и фрагментов программного кода.  Программные фрагменты предоставляют значения для переменных частей строки и управляют условными и повторяющимися частями.  
  
 Например, следующий шаблон можно использовать в приложении, создающем HTML\-отчет.  
  
```  
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
  
 Обратите внимание, что шаблон — это страница HTML, в которой переменные части были заменены программным кодом.  Начать создание такой страницы можно с написания статического прототипа страницы HTML.  Затем можно заменить таблицу и другие переменные части программным кодом, который генерирует содержимое, варьирующееся от случая к случаю.  
  
 Благодаря использованию шаблона в приложении проще увидеть окончательную форму выходных данных, чем, к примеру, при использовании длинной последовательности инструкций write.  В этом случае можно проще и более надежно менять форму выходных данных.  
  
## Создание текстового шаблона времени выполнения в любом приложении  
  
#### Создание текстового шаблона времени выполнения  
  
1.  В обозревателе решений, в контекстном меню проекта выберите  **Добавить**,  **Новый элемент**.  
  
2.  В  **Добавить новый элемент** выберите  **Текст шаблона во время выполнения**.  \(В [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] см. в разделе **Common Items\\General**.\)  
  
3.  Введите имя файла шаблона.  
  
    > [!NOTE]
    >  Имя файла шаблона будет использоваться как имя класса в сгенерированном коде.  Поэтому оно не должно содержать пробелов и знаков препинания.  
  
4.  Выберите  **Добавить**.  
  
     Будет создан новый файл с расширением **.tt**.  Его свойство **Специальный инструмент** будет иметь значение **TextTemplatingFilePreprocessor**.  Он содержит следующие строки:  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## Преобразование существующего файла в шаблон времени выполнения  
 Удобный способ создания шаблона — преобразование имеющегося примера выходных данных.  Например, если приложение будет генерировать HTML\-файлы, можно начать с создания обычного HTML\-файла.  Убедитесь, что он правильно работает и его представление является верным.  Затем включите его в проект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и преобразуйте в шаблон.  
  
#### Преобразование существующего текстового файла в шаблон времени выполнения  
  
1.  Включите файл в проект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  В обозревателе решений, в контекстном меню проекта выберите  **Добавить**,  **Существующий элемент**.  
  
2.  Свойству **Специальные инструменты** этого файла присвойте значение **TextTemplatingFilePreprocessor**.  В обозревателе решений, в контекстном меню файл, выберите  **Свойства**.  
  
    > [!NOTE]
    >  Если это свойство уже установлено, убедитесь, что оно имеет значение **TextTemplatingFilePreprocessor**, а не **TextTemplatingFileGenerator**.  Так может случиться, если вы включили файл, уже имеющий расширение **.tt**.  
  
3.  Измените расширение имени файла на **.tt**.  Хотя этот шаг является необязательным, он позволяет избежать открытия файла в неподходящем редакторе.  
  
4.  Удалите из основной части имени файла все пробелы и знаки препинания.  Например, имя "My Web Page.tt" было бы неверным, а имя "MyWebPage.tt" годится.  Имя файла будет использоваться как имя класса в сгенерированном коде.  
  
5.  В начало файла вставьте следующую строку:  Если вы работаете в проекте Visual Basic, замените "C\#" на "VB".  
  
     `<#@ template language="C#" #>`  
  
## Содержимое шаблона времени выполнения  
  
### Директива template  
 Сохраните первую строку шаблона в том виде, в каком она была при создании файла:  
  
 `<#@ template language="C#" #>`  
  
 Параметр language будет зависеть от языка проекта.  
  
### Чистое содержимое  
 Отредактируйте файл **.tt**, чтобы он содержал только текст, который должно генерировать приложение.  Примеры.  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### Внедренный программный код  
 Программный код можно вставлять между тегами `<#` и `#>`.  Примеры.  
  
```c#  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb#  
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
  
 Обратите внимание, что инструкции вставляются между тегами `<# ... #>`, а выражения – между `<#= ... #>`.  Дополнительные сведения см. в разделе [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
## Использование шаблона  
  
### Код, формируемый на основе шаблона  
 При сохранении файла **.tt** генерируется дочерний файл **.cs** или **.vb**.  Чтобы просмотреть этот файл в обозревателе решений, разверните узел файла **.tt**.  В проекте Visual Basic возможность развернуть этот узел появится после того, как вы щелкните **Показать все файлы** на панели инструментов обозревателя решений.  
  
 Заметьте, что этот дочерний файл содержит разделяемый класс, имеющий метод с именем `TransformText()`.  Этот метод можно вызвать из приложения.  
  
### Генерирование текста во время выполнения  
 В коде приложения можно генерировать содержимое шаблона с использованием таких вызовов:  
  
```c#  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb#  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 Чтобы поместить созданный класс в определенном пространстве имен, задайте значение для свойства **Пространство имен специального инструмента** в файле текстового шаблона.  
  
### Отладка во время выполнения текстовых шаблонов  
 Отладка и тестирование текстовые шаблоны во время выполнения таким же образом, как обычный код.  
  
 Можно установить точку останова в текст шаблона.  Если запустить приложение в режиме отладки из Visual Studio можно пошаговое выполнение кода и оценки выражений смотреть обычным способом.  
  
### Передача параметров в конструкторе  
 Обычно шаблон должен импортировать некоторые данные из других частей приложения.  Чтобы облегчить эту задачу, генерируемый на основе шаблона код создается в виде разделяемого класса.  Можно создать другую часть этого класса в другом файле проекта.  Этот файл может содержать конструктор с параметрами, свойства и функции, доступные как из внедренного в шаблон кода, так и из остальной части приложения.  
  
 Например, можно создать отдельный файл **MyWebPageCode.cs**:  
  
```c#  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 В файле шаблона **MyWebPage.tt** можно написать:  
  
```c#  
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
  
 Использование этого шаблона в приложении  
  
```c#  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### Параметры конструктора в Visual Basic  
 В [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] отдельный файл **MyWebPageCode.vb** содержит следующее:  
  
```vb#  
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
  
```vb#  
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
  
 Шаблон в этом случае вызывается передачей параметров в конструктор:  
  
```vb#  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### Передача данных в свойства шаблона  
 Альтернативным способом передачи данных шаблону является добавление в класс шаблона открытых свойств в частичном определении класса.  Перед вызовом метода `TransformText()` приложение может задать свойства.  
  
 Кроме того, в класс шаблонов можно добавить поля в виде частичного определения.  В этом случае можно выполнять передачу данных между последовательными выполнениями шаблона.  
  
### Использование разделяемого класса для кода  
 Многие разработчики предпочитают не включать в шаблоны крупные фрагменты кода.  Вместо этого определяются методы в разделяемом классе, имя которого совпадает с именем файла шаблона.  Вызовите эти методы из шаблона.  В этом случае в шаблоне лучше видно, как будет выглядеть целевая выходная строка.  Обсуждения внешнего вида результата можно отделить от логики создания данных, которые отображаются в этом результате.  
  
### Сборки и ссылки  
 Если требуется, чтобы код шаблона ссылался на сборку .NET или другую сборку, такую как **System.Xml.dll**, нужно добавить ее в раздел **Ссылки** проекта обычным образом.  
  
 Если требуется импортировать пространство имен таким же образом, как это делается с использованием инструкции `using`, можно воспользоваться директивой `import`:  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 Эти директивы должны размещаться в начале файла, сразу за директивой `<#@template`.  
  
### Общее содержимое  
 Если имеется текст, который должен использоваться в нескольких шаблонах, можно разместить его в отдельном файле и включать в каждый файл, где он должен присутствовать:  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 Включаемое содержимое может содержать любое сочетание программного кода и обычного текста, а также другие директивы include и прочие директивы.  
  
 Директива include может использоваться в любой части текста файла шаблона или включаемого файла.  
  
### Наследование текстовых шаблонов времени выполнения  
 Можно настроить обмен содержимым между шаблонами времени выполнения, создав шаблон базового класса, который может быть абстрактным.  Использование `inherits` параметр `<@#template#>` директивы для ссылки на другой класс шаблона во время выполнения.  
  
#### Шаблон наследования: фрагменты в базовых методах  
 В шаблоне, использованном в следующем примере, обратите внимание на следующее:  
  
-   Базовый класс `SharedFragments` определяет методы в составе блоков функций класса `<#+ ... #>`.  
  
-   Базовый класс не содержит текста в свободной форме.  Все его текстовые блоки размещены внутри методов функций класса.  
  
-   Производный класс вызывает методы, определенные в базовом классе `SharedFragments`.  
  
-   Приложение вызывает метод `TextTransform()` производного класса, но не преобразует базовый класс `SharedFragments`.  
  
-   Базовый и производный классы являются текстовые шаблоны во время выполнения:,  **Пользовательский инструмент** свойству  **TextTemplatingFilePreprocessor**.  
  
 **SharedFragments.tt:**  
  
```c#  
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
  
```c#  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```c#  
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
  
#### Шаблон наследования: текст в основной части базового шаблона  
 Этот подход является альтернативой использованию наследования шаблонов и предполагает определение массива текста в базовом шаблоне.  Производные шаблон предоставляют фрагменты данных и текста, которые вставляются в базовое содержимое.  
  
 **AbstractBaseTemplate1.tt:**  
  
```c#  
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
  
```c#  
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
  
```c#  
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
  
## Связанные разделы  
 Шаблоны времени разработки: если требуется использовать шаблон для генерирования кода, который станет частью приложения, см. раздел [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Шаблоны во время выполнения можно использовать в любом приложении, где определить шаблоны и их содержимого во время компиляции.  Однако если требуется написать расширение [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], генерирующее текст из шаблонов, изменяющихся во время выполнения, см. раздел [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## См. также  
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)   
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)   
 [Общее представление о T4: Предварительная обработка текстовых шаблонов, г\-н Олег Sych](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)