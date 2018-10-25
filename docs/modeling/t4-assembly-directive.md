---
title: Директива Assembly T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: cd7f1f36374f3411b5a76f5df5e3e25bb52df230
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948646"
---
# <a name="t4-assembly-directive"></a>Директива Assembly T4

В Visual Studio во время разработки текстового шаблона `assembly` директива загружает сборку, чтобы код шаблона можно использовать ее типы. Действует аналогично добавлению ссылки на сборку в проект Visual Studio.

 Общие сведения о создании текстовых шаблонов, см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
>  В текстовом шаблоне времени выполнения (предварительно обработанном) директива `assembly` не требуется. Вместо этого добавить нужные сборки **ссылки** проекта Visual Studio.

## <a name="using-the-assembly-directive"></a>Использование директивы Assembly
 Синтаксис директивы таков:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Имя сборки должно быть одним из следующих:

- Строгое имя сборки в глобальном кэше сборок, такое как `System.Xml.dll`. Кроме того, можно использовать полную форму, такую как `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Дополнительные сведения см. в разделе <xref:System.Reflection.AssemblyName>.

- абсолютный путь к сборке;

  Можно использовать `$(variableName)` синтаксис, чтобы ссылаться на переменные Visual Studio, такие как `$(SolutionDir)`, и `%VariableName%` для ссылки на переменные среды. Пример:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 В предварительно преобразованном текстовом шаблоне директива assembly не производит никакого эффекта. Вместо этого, включите необходимые ссылки в **ссылки** раздел проекта Visual Studio. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="standard-assemblies"></a>Стандартные сборки
 Следующие сборки загружаются автоматически, поэтому для них не нужно создавать директивы сборки:

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  При использовании пользовательской директивы процессор директив может загружать дополнительные сборки. Например, при создании шаблонов для доменного языка (DSL) не требуется создавать директивы сборки для следующих сборок:

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- Сборка, содержащая DSL.

## <a name="msbuild"></a> Использование свойств проекта в MSBuild и Visual Studio
 Макросы Visual Studio, например $ (solutiondir) не работают в MSBuild. Если требуется преобразовывать шаблоны на компьютере сборки, необходимо использовать свойства проекта.

 Измените CSPROJ- или VBPROJ-файл для определения свойства проекта. В этом примере определяется свойство с именем `myLibFolder`.

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Теперь можно использовать свойство проекта в текстовых шаблонах, которые будут правильно преобразовываться как в Visual Studio, так и в MSBuild:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>См. также

- [Директива Include T4](../modeling/t4-include-directive.md)