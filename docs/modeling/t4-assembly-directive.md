---
title: Директива Assembly T4
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c08518d3bcff8d91cc8fabebe7b858c5880ce5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671036"
---
# <a name="t4-assembly-directive"></a>Директива Assembly T4

В текстовом шаблоне времени разработки Visual Studio директива `assembly` загружает сборку, чтобы код шаблона мог использовать его типы. Этот результат аналогичен добавлению ссылки на сборку в проекте Visual Studio.

 Общие сведения о создании текстовых шаблонов см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> В текстовом шаблоне времени выполнения (предварительно обработанном) директива `assembly` не требуется. Вместо этого добавьте необходимые сборки в **ссылки** проекта Visual Studio.

## <a name="using-the-assembly-directive"></a>Использование директивы Assembly
 Синтаксис директивы таков:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Имя сборки должно быть одним из следующих:

- Строгое имя сборки в глобальном кэше сборок, такое как `System.Xml.dll`. Кроме того, можно использовать полную форму, такую как `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Для получения дополнительной информации см. <xref:System.Reflection.AssemblyName>.

- абсолютный путь к сборке;

  Синтаксис `$(variableName)` можно использовать для ссылки на переменные среды Visual Studio, такие как `$(SolutionDir)`, а также для `%VariableName%` ссылок на них. Пример:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 В предварительно преобразованном текстовом шаблоне директива assembly не производит никакого эффекта. Вместо этого включите необходимые ссылки в раздел **References** проекта Visual Studio. Дополнительные сведения см. [в разделе Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

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

## <a name="msbuild"></a>Использование свойств проекта в MSBuild и Visual Studio
 Макросы Visual Studio, такие как $ (SolutionDir), не работают в MSBuild. Если требуется преобразовывать шаблоны на компьютере сборки, необходимо использовать свойства проекта.

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

## <a name="see-also"></a>См. также раздел

- [Директива Include T4](../modeling/t4-include-directive.md)