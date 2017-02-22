---
title: "Практическое руководство. Инкрементное построение | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "инкрементные построения"
  - "MSBuild, инкрементное построение"
  - "MSBuild, инкрементные построения"
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Практическое руководство. Инкрементное построение
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При построении большого проекта важно не перестраивать ранее созданные компоненты, которые все еще актуальны.  Если каждый раз создавать все целевые объекты, выполнение каждого построения будет занимать очень много времени.  Для выполнения инкрементных построений \(построений, в которых перестраиваются только целевые объекты, не строившиеся ранее, или целевые объекты, ставшие неактуальными\) [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) может сравнить штампы времени входных файлов со штампами времени выходных файлов и определить, следует ли пропустить, построить или частично перестроить целевой объект.  Однако при этом необходимо взаимно однозначное сопоставление входных и выходных данных.  Можно использовать преобразования, чтобы целевые объекты могли идентифицировать это прямое сопоставление.  Дополнительные сведения о преобразованиях см. в разделе [Transform](../msbuild/msbuild-transforms.md).  
  
## Указание входных и выходных данных  
 Для целевого объекта можно использовать инкрементное построение, если в файле проекта указаны входные и выходные данные.  
  
#### Указание входных и выходных данных для целевого объекта  
  
-   Используйте атрибуты `Inputs` и `Outputs` элемента `Target`.  Например:  
  
    ```  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] может сравнить штампы времени файлов входных данных со штампами времени файлов выходных данных и определить, следует ли пропустить, построить или частично перестроить целевой объект.  В следующем примере, если какой\-либо файл в списке элементов `@(CSFile)` новее файла hello.exe, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] запустит целевой объект; в противном случае целевой объект будет пропущен.  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Когда в целевом объекте указаны входные и выходные данные, то либо каждый выходной файл можно сопоставить только с одним входным файлом, либо между входными и выходными данными невозможно установить прямое сопоставление.  Например, в предыдущей задаче [Задача Csc](../msbuild/csc-task.md) выходной файл hello.exe нельзя сопоставить с каким\-либо отдельным входным файлом, поскольку он зависит от всех этих файлов.  
  
> [!NOTE]
>  Для целевого объекта, в котором отсутствует прямое сопоставление между входными и выходными данными, построение всегда будет выполняться чаще, чем для целевого объекта, в котором с каждым выходным файлом можно сопоставить только один входной, поскольку [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] не сможет определить, какие выходные данные необходимо перестроить, если изменены некоторые входные данные.  
  
 Задачи, в которых можно определить прямое сопоставление между выходными и входными данными, например, [Задача LC](../msbuild/lc-task.md), наилучшим образом подходят для инкрементных сборок в отличие от таких задач, как `Csc` и [Vbc](../msbuild/vbc-task.md), в которых на выходе создается сборка из ряда входных файлов.  
  
## Пример  
 В следующем примере используется проект, в котором выполняется сборка файлов справки для гипотетической справочной системы.  В проекте выполняется преобразование исходных TXT\-файлов в промежуточные CONTENT\-файлы, которые затем комбинируются с XML\-файлами метаданных для получения итогового HELP\-файла, используемого справочной системой.  В проекте применяются следующие гипотетические задачи:  
  
-   `GenerateContentFiles`: преобразует TXT\-файлы в CONTENT\-файлы.  
  
-   `BuildHelp`: объединяет CONTENT\-файлы и XML\-файлы метаданных для построения итогового HELP\-файла.  
  
 В проекте используются преобразования для создания взаимно однозначного сопоставления между входными и выходными данными в задаче `GenerateContentFiles`.  Дополнительные сведения см. в разделе [Transform](../msbuild/msbuild-transforms.md).  К тому же элемент `Output` настраивается на автоматическое использование выходных данных задачи `GenerateContentFiles` в качестве входных данных для задачи `BuildHelp`.  
  
 В файле проекта содержатся целевые объекты `Convert` и `Build`.  Задачи `GenerateContentFiles` и `BuildHelp` помещаются соответственно в целевые объекты `Convert` и `Build`, так что для каждого целевого объекта возможна инкрементная сборка.  С помощью элемента `Output` выходные данные задачи `GenerateContentFiles` помещаются в список элементов `ContentFile`, где они могут использоваться в качестве входных данных для задачи `BuildHelp`.  Таким образом, благодаря использованию элемента `Output` выходные данные одной задачи предоставляются в качестве входных данных для другой задачи, так что вам не нужно вручную перечислять отдельные элементы или списки элементов в каждой задаче.  
  
> [!NOTE]
>  Хотя для целевого объекта `GenerateContentFiles` возможно инкрементное построение, все выходные данные этого целевого объекта требуются в качестве входных данных для целевого объекта `BuildHelp`.  При использовании элемента `Output` [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] автоматически предоставляет все выходные данные одного целевого объекта в качестве входных данных для другого объекта.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## См. также  
 [Целевые объекты](../msbuild/msbuild-targets.md)   
 [Элемент Target \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Transform](../msbuild/msbuild-transforms.md)   
 [Задача Csc](../msbuild/csc-task.md)   
 [Задача Vbc](../msbuild/vbc-task.md)