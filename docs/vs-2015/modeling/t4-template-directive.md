---
title: Директива шаблона T4 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2b0a8e04-6fee-4c6c-b086-e49fc728a3ed
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3a17275730cd093f8f9fa433aa28c7f9ca86e80
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298139"
---
# <a name="t4-template-directive"></a>Директива Template T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Как правило, текстовый шаблон T4 в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] начинается с директивы `template`, которая задает способ обработки шаблона. В каждом текстовом шаблоне и файлах, которые он содержит, может присутствовать только одна директива шаблона.

 Общие сведения о создании текстовых шаблонов см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template-directive"></a>Применение директивы Template

```
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>
```

 Директива `template` имеет несколько атрибутов, позволяющих задавать разные аспекты преобразования. Ни один атрибут не является обязательным.

## <a name="compileroptions-attribute"></a>атрибут compilerOptions
 Пример: `compilerOptions="optimize+"`

 Допустимые значения: любые допустимые параметры компилятора. Дополнительные сведения см. в разделе [ C# параметры компилятора, упорядоченные по категориям](https://msdn.microsoft.com/library/96437ecc-6502-4cd3-b070-e9386a298e83) и [Visual Basic параметры компилятора, перечисленные по категориям](https://msdn.microsoft.com/library/fbe36f7a-7cfa-4f77-a8d4-2be5958568e3).

 Игнорируется для шаблонов времени выполнения (предварительно обработанных).

 Эти параметры применяются, если шаблон преобразован в [!INCLUDE[csprcs](../includes/csprcs-md.md)] или [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] и компилируется полученный код.

## <a name="culture-attribute"></a>атрибут culture
 Пример: `culture="de-CH"`

 Допустимые значения: "", инвариантный язык и региональные параметры, используемые по умолчанию.

 Язык и региональные параметры задаются как строка в форме xx-XX. Например: en-US, ja-JP, de-CH, de-DE. Дополнительные сведения см. в разделе <xref:System.Globalization.CultureInfo?displayProperty=fullName>.

 Этот атрибут задает язык и региональные параметры для использования при преобразовании блока выражений в текст.

## <a name="debug-attribute"></a>атрибут debug
 Пример.

```
debug="true"
```

 Допустимые значения: `true, false`. Значение по умолчанию — false.

 Если атрибут `debug` имеет значение `true`, промежуточный файл кода содержит сведения, позволяющие отладчику точнее определить положение прерывания или исключения в шаблоне.

 Для шаблонов времени разработки промежуточный файл кода будет записан в каталог **% TEMP%** .

 Чтобы запустить шаблон времени разработки в отладчике, сохраните текстовый шаблон, откройте контекстное меню текстового шаблона в обозреватель решений и выберите **Отладка шаблона T4**.

## <a name="hostspecific-attribute"></a>атрибут hostspecific
 Пример.

```
hostspecific="true"
```

 Допустимые значения: `true, false, trueFromBase`. Значение по умолчанию — false.

 Если задать для этого атрибута значение `true`, свойство с именем `Host` будет добавлено в класс, сгенерированный текстовым шаблоном. Свойство является ссылкой на узел подсистемы преобразования и объявляется как [итексттемплатинженгинехост](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Если определено пользовательское основное приложение, можно выполнить его приведение к типу пользовательского основного приложения.

 Поскольку тип данного свойства зависит от типа основного приложения, оно полезно, только если пишется текстовый шаблон, работающий с конкретным основным приложением. Он применим к [шаблонам времени разработки](../modeling/design-time-code-generation-by-using-t4-text-templates.md), но не к [шаблонам времени выполнения](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Когда свойство `hostspecific` имеет значение `true` и вы используете [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно привести `this.Host` к типу IServiceProvider для доступа к функциям [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Кроме того, можно воспользоваться `Host.ResolvePath(filename)` для получения абсолютного пути к файлу в проекте. Пример.

```csharp
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#@ import namespace="System.IO" #>
<# // Get the Visual Studio API as a service:
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

<#
 // Find a path within the current project:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>

```

 Если атрибуты `inherits` и `hostspecific` используются совместно, укажите host="trueFromBase" в производном классе и host="true" в базовом классе. Это позволит избежать двойного определения свойства `Host` в созданном коде.

## <a name="language-attribute"></a>атрибут language
 Пример: `language="VB"`

 Допустимые значения: `C#` (по умолчанию)

 `VB`

 Атрибут Language задает язык ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] или [!INCLUDE[csprcs](../includes/csprcs-md.md)]), используемый для исходного кода в блоках операторов и выражений. Этот язык будет использоваться в промежуточном файле кода, из которого создаются выходные данные. Этот язык не связан с языком, создаваемым шаблоном, который может быть представлен любым видом текста.

 Пример.

```vb
<#@ template language="VB" #>
<#@ output extension=".txt" #>
Squares of numbers:
<#
  Dim number As Integer
  For number = 1 To 4
#>
  Square of <#= number #> is <#= number * number #>
<#
  Next number
#>

```

## <a name="inherits-attribute"></a>атрибут inherits
 Можно задать наследование программного кода шаблона от другого класса, который также может быть создан из текстового шаблона.

### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>Наследование в текстовом шаблоне времени выполнения (предварительно обработанном)
 Можно использовать наследование между текстовыми шаблонами времени выполнения для создания базового шаблона с несколькими производными вариантами. Шаблоны времени выполнения — это те, для которых свойство **Custom Tool** имеет значение **тексттемплатингфилепрепроцессор**. Шаблон времени выполнения создает код, который можно вызывать в приложении для создания текста, который определен в шаблоне. Дополнительные сведения см. [в разделе Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Если атрибут `inherits` не задан, базовый и производный классы создаются из текстового шаблона. При задании атрибута `inherits` создается только производный класс. Можно создать базовый класс вручную, однако он должен предоставлять методы, используемые производным классом.

 Как правило, в качестве базового класса указывается другой предварительно обработанный шаблон. Базовый шаблон предоставляет общие блоки текста, которые могут чередоваться с текстом из производных шаблонов. Можно использовать блоки возможностей класса `<#+ ... #>`, чтобы определить методы, содержащие фрагменты текста. Например, можно поместить структуру выходного текста в базовый шаблон и предоставить виртуальные методы, которые могут переопределяться в производных шаблонах:

 Текстовый шаблон времени выполнения (предварительно обработанный) BaseTemplate.tt:

```scr
This is the common header.
<#
  SpecificFragment1();
#>
A common central text.
<#
  SpecificFragment2();
#>
This is the common footer.
<#+
  // Declare abstract methods
  protected virtual void SpecificFragment1() { }
  protected virtual void SpecificFragment2() { }
#>

```

 Текстовый шаблон времени выполнения (предварительно обработанный) DerivedTemplate1.tt:

```csharp
<#@ template language="C#" inherits="BaseTemplate" #>
<#
  // Run the base template:
  base.TransformText();
#>
<#+
// Provide fragments specific to this derived template:
protected override void SpecificFragment1()
{
#>
   Fragment 1 for DerivedTemplate1
<#+
}
protected override void SpecificFragment2()
{
#>
   Fragment 2 for DerivedTemplate1
<#+
}
#>

```

 Код приложения для вызова DerivedTemplate1:

```csharp
Console.WriteLine(new DerivedTemplate().TransformText());
```

 Полученные выходные данные:

```
This is the common header.
   Fragment 1 for DerivedTemplate1
A common central text.
   Fragment 2 for DerivedTemplate1
This is the common footer.
```

 Можно создавать базовый и производный классы в разных проектах. Не забудьте добавить базовый проект или сборку в ссылки производного проекта.

 Кроме того, в качестве базового класса можно использовать обычный, созданный вручную класс. Базовый класс должен предоставлять методы, используемые производным классом.

> [!WARNING]
> Если атрибуты `inherits` и `hostspecific` используются совместно, укажите hostspecific="trueFromBase" в производном классе и host="true" в базовом классе. Это позволит избежать двойного определения свойства `Host` в созданном коде.

### <a name="inheritance-in-a-design-time-text-template"></a>Наследование в текстовом шаблоне времени разработки
 Текстовый шаблон времени разработки — это файл, для которого **пользовательское средство** имеет значение **тексттемплатингфилеженератор**. Этот шаблон позволяет создать выходной файл кода или текста, формирующего часть проекта [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. При создании выходного файла шаблон сначала преобразуется в промежуточный файл программного кода, который обычно не видно пользователю. Атрибут `inherits` задает базовый класс для данного промежуточного кода.

 Для текстового шаблона времени разработки можно задать любой базовый класс, наследуемый от <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Воспользуйтесь директивой `<#@assembly#>` для загрузки сборки или проекта, содержащего базовый класс.

 Дополнительные сведения см. [в разделе "наследование в текстовых шаблонах" в блоге Гарет Jones "](https://go.microsoft.com/fwlink/?LinkId=208373).

## <a name="linepragmas-attribute"></a>Атрибут LinePragmas
 Пример: `linePragmas="false"`

 Допустимые значения: `true` (по умолчанию)

 `false`

 Если для этого атрибута установлено значение false, удаляются теги, задающие номера строк в созданном коде. Это означает, что компилятор сообщает о любых ошибках с указанием номеров строк созданного кода. Таким образом расширяются возможности отладки, позволяя выбирать отладку текстового шаблона или созданного кода.

 Этот атрибут также может помочь, если вы считаете, что абсолютные имена файлов в директивах pragma вызывают отвлекающие слияния в системе управления исходным кодом.

## <a name="visibility-attribute"></a>Атрибут Visibility
 Пример: `visibility="internal"`

 Допустимые значения: `public` (по умолчанию)

 `internal`

 В текстовом шаблоне времени выполнения задает атрибут видимости созданного класса. По умолчанию класс является частью открытого API кода, но если задать значение `visibility="internal"`, только ваш код сможет использовать класс, создающий текст.
