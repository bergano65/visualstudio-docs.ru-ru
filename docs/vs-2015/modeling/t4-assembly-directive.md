---
title: T4 Директива Assembly | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f81bdcad4f255585c2c554add59ed04dea5872d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993131"
---
# <a name="t4-assembly-directive"></a>Директива Assembly T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В текстовом шаблоне времени проектирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] директива `assembly` загружает сборку, чтобы в коде шаблона можно было использовать ее типы. Это дает эффект, аналогичный добавлению ссылки на сборку в проекте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Общие сведения о создании текстовых шаблонов, см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  В текстовом шаблоне времени выполнения (предварительно обработанном) директива `assembly` не требуется. Вместо этого добавить нужные сборки **ссылки** из вашей [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проекта.  
  
## <a name="using-the-assembly-directive"></a>Использование директивы Assembly  
 Синтаксис директивы таков:  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 Имя сборки должно быть одним из следующих:  
  
- Строгое имя сборки в глобальном кэше сборок, такое как `System.Xml.dll`. Кроме того, можно использовать полную форму, такую как `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Дополнительные сведения см. в разделе <xref:System.Reflection.AssemblyName>.  
  
- абсолютный путь к сборке;  
  
  Синтаксис `$(variableName)` можно использовать для ссылки на переменные [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], такие как `$(SolutionDir)`, а синтаксис `%VariableName%` — для ссылки на переменные среды. Пример:  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 В предварительно преобразованном текстовом шаблоне директива assembly не производит никакого эффекта. Вместо этого, включите необходимые ссылки в **ссылки** часть вашей [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проекта. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
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
  
##  <a name="msbuild"></a> Использование свойств проекта в MSBuild и Visual Studio  
 Макросы Visual Studio, такие как $(SolutionDir), не работают в MSBuild. Если требуется преобразовывать шаблоны на компьютере сборки, необходимо использовать свойства проекта.  
  
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
 [Директива Include T4](../modeling/t4-include-directive.md)
