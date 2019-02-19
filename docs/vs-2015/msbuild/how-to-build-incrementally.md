---
title: Практическое руководство. Инкрементное построение | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b1bcb8752d8defacadc641f55594e354e081d5cb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803914"
---
# <a name="how-to-build-incrementally"></a>Практическое руководство. Инкрементное построение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
При сборке большого проекта важно, чтобы созданные ранее компоненты, которые все еще актуальны, не перестраивались. Если каждый раз создаются все целевые объекты, каждая сборка будет занимать много времени. Для выполнения инкрементных построений (сборки, в которых перестраиваются только те целевые объекты, которые не были построены ранее, или устаревшие целевые объекты) [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) может сравнить метки времени входных файлов с метками времени выходных файлов и определить, следует ли пропустить, построить или частично перестроить целевой объект. Однако должно быть однозначное сопоставление между входными и выходными данными. Чтобы целевые объекты могли идентифицировать это прямое сопоставление, можно использовать преобразования. Дополнительные сведения о преобразованиях см. в статье [Преобразования](../msbuild/msbuild-transforms.md).  
  
## <a name="specifying-inputs-and-outputs"></a>Указание входных и выходных данных  
 Целевой объект можно построить инкрементно, если в файле проекта указаны входные и выходные данные.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Указание входных и выходных данных для целевого объекта  
  
- Используйте атрибуты `Inputs` и `Outputs` для элемента `Target`. Например:  
  
  ```  
  <Target Name="Build"  
      Inputs="@(CSFile)"  
      Outputs="hello.exe">  
  ```  
  
  [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может сравнить метки времени входных файлов с метками времени выходных файлов и определить, следует ли пропустить, построить или частично перестроить целевой объект. В следующем примере, если какой-либо файл в списке элементов `@(CSFile)` новее, чем файл hello.exe, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] запустит целевой объект; в противном случае он будет пропущен.  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Когда в целевом объекте указаны входные и выходные данные, все выходные данные можно сопоставить только с одними входными данными, либо между выходными и входными данными может отсутствовать прямое сопоставление. В предыдущей [задаче Csc](../msbuild/csc-task.md), например, выходные данные, hello.exe, нельзя сопоставить с отдельными выходными данными — это зависит от всех остальных.  
  
> [!NOTE]
>  Для целевого объекта, в котором нет прямого сопоставления между входными и выходными данными, построение всегда будет выполняться чаще, чем для целевого объекта, в котором все выходные данные можно сопоставить только с одними входными данными, поскольку [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] не сможет определить какие выходные данные необходимо перестроить, если изменены некоторые входные данные.  
  
 Задачи, в которых можно определить прямое сопоставление между выходными и входными данными, такие как [задача LC](../msbuild/lc-task.md), лучше всего подходят для инкрементных сборок в отличие от задач, таких как `Csc` и [Vbc](../msbuild/vbc-task.md), в которых из ряда входных данных создается только одна выходная сборка.  
  
## <a name="example"></a>Пример  
 В следующем примере используется проект, который создает файлы справки для гипотетической справочной системы. В проекте выполняется преобразование исходных TXT-файлов в промежуточные CONTENT-файлы, которые затем объединяются с XML-файлами метаданных для получения итогового HELP-файла, используемого в справке. В проекте используются следующие гипотетические задачи.  
  
- `GenerateContentFiles`: преобразует TXT-файлы в CONTENT-файлы.  
  
- `BuildHelp`: объединяет CONTENT-файлы и XML-файлы метаданных для построения итогового HELP-файла.  
  
  В проекте используются преобразования для создания взаимно однозначного сопоставления между входными и выходными данными в задаче `GenerateContentFiles`. Дополнительные сведения см. в статье [Преобразования](../msbuild/msbuild-transforms.md). Кроме того, элемент `Output` настроен на автоматическое использование выходных данных задачи `GenerateContentFiles` в качестве входных данных для задачи `BuildHelp`.  
  
  Этот файл проекта содержит оба целевых объекта `Convert` и `Build`. Задачи `GenerateContentFiles` и `BuildHelp` помещаются в целевые объекты `Convert` и `Build` соответственно, чтобы все целевые объекты можно было построить инкрементно. Используя элемент `Output`, выходные данные задачи `GenerateContentFiles` помещаются в список элементов `ContentFile`, где они могут использоваться в качестве входных данных для задачи `BuildHelp`. Использование элемента `Output` таким образом позволяет автоматически представить выходные данные одной задачи в качестве входных данных для другой задачи, что исключает необходимость в перечислении отдельных элементов или списков элементов вручную в каждой задаче.  
  
> [!NOTE]
>  Несмотря на то что для целевого объекта `GenerateContentFiles` используется инкрементное построение, все выходные данные этого целевого объекта всегда требуются в качестве входных данных для целевого объекта `BuildHelp`. При использовании элемента `Output` [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] автоматически предоставляет все выходные данные одного целевого объекта в качестве входных данных для другого целевого объекта.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Целевые объекты](../msbuild/msbuild-targets.md)   
 [Элемент Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Преобразования](../msbuild/msbuild-transforms.md)   
 [Задача Csc](../msbuild/csc-task.md)   
 [Задача Vbc](../msbuild/vbc-task.md)
