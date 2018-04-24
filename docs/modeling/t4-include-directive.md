---
title: Директива Include T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2a7b6d52d89da2b838d580bc2dbad9e36b9c73b9
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="t4-include-directive"></a>Директива Include T4

В текстовый шаблон в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно включить текст из другого файла, воспользовавшись директивой `<#@include#>`. Директивы `include` можно разместить в любом месте текстового шаблона перед первым блоком функций класса `<#+ ... #>`. Включенные файлы также могут содержать директивы `include` и другие директивы. Это позволяет использовать один и тот же код шаблона и стандартный текст в нескольких шаблонах.

## <a name="using-include-directives"></a>Использование директив Include

```
<#@ include file="filePath" [once="true"] #>
```

-   Путь `filePath` может быть абсолютным или относительным для текущего файла шаблона.

     Кроме того, отдельные расширения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] могут задавать собственные каталоги для поиска включенных файлов. Например, при установке визуализации и моделирования SDK (Инструменты DSL) следующую папку добавляется в список включения: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.

     Эти дополнительные папки включения могут зависеть от расширения включающего файла. Например, папка включения DSL Tools доступна только для включающих файлов с расширением `.tt`.

-   `filePath` может включать переменные среды, отделенные знаком "%". Пример:

    ```
    <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
    ```

-   В имени включенного файла не обязательно использовать расширение `".tt"`.

     Для включенных файлов можно использовать другое расширение, например `".t4"`. Это происходит потому, что при добавлении `.tt` файл к проекту [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически устанавливает его **пользовательский инструмент** свойства `TextTemplatingFileGenerator`. Как правило, не нужно, чтобы включенные файлы преобразовывались по отдельности.

     С другой стороны, нужно помнить, что в некоторых случаях расширение файла влияет на то, в каких дополнительных папках будет выполнен поиск файлов включения. Это может оказаться важным при наличии включенного файла, содержащего другие файлы.

-   Включенное содержимое обрабатывается почти так же, как если бы оно было частью включающего текстового шаблона. Однако можно включить файл, содержащий блок функций класса `<#+...#>`, даже если за директивой `include` следуют обычный текст и стандартные управляющие блоки.

-   Используйте `once="true"` для убедитесь, что шаблон включен только один раз, даже если он вызывался из нескольких других файлов include.

     Это делает компонент, его легко встраивать библиотеку для повторного использования T4 фрагментов, которую можно включить в будет задумываясь, другие фрагмент кода уже включила их.  Например предположим, что имеется библиотека детальный фрагменты кода, обрабатывающих обработки шаблона и создания C#.  В свою очередь они используются некоторые программы более конкретных задач, таких как создание исключений, которые затем можно использовать из любой шаблон более от приложения. Если нарисовать граф зависимостей, можно увидеть, что некоторые фрагменты кода были бы включены несколько раз. Но параметр `once` предотвращает последующие включения.

 **MyTextTemplate.tt:**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>

```

 **TextFile1.t4:**

```
   Output Message 2 (from included file).
<#@include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>

```

 **TextFile2.t4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>

```

 **Сгенерированный в результате файл, MyTextTemplate.txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).

```

##  <a name="msbuild"></a> Использование свойств проекта в MSBuild и Visual Studio
 Несмотря на то, что в директиве include можно использовать макросы Visual Studio, такие как $ (solutiondir), они не работают в MSBuild. Если требуется преобразовывать шаблоны на компьютере сборки, необходимо использовать свойства проекта.

 Измените CSPROJ- или VBPROJ-файл для определения свойства проекта. В этом примере определяется свойство с именем `myIncludeFolder`.

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>

```

 Теперь можно использовать свойство проекта в текстовых шаблонах, которые будут правильно преобразовываться как в Visual Studio, так и в MSBuild:

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```