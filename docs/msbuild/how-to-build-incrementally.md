---
title: Практическое руководство. Инкрементная сборка | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e78ce202c04b8b2af60a7b3d09b149c7e02f2e50
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977363"
---
# <a name="how-to-build-incrementally"></a>Практическое руководство. Инкрементная сборка
При сборке большого проекта важно, чтобы созданные ранее компоненты, которые все еще актуальны, не перестраивались. Если каждый раз создаются все целевые объекты, каждая сборка будет занимать много времени. Для выполнения инкрементных построений (сборки, в которых перестраиваются только те целевые объекты, которые не были построены ранее, или устаревшие целевые объекты) [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) может сравнить метки времени входных файлов с метками времени выходных файлов и определить, следует ли пропустить, построить или частично перестроить целевой объект. Однако должно быть однозначное сопоставление между входными и выходными данными. Чтобы целевые объекты могли идентифицировать это прямое сопоставление, можно использовать преобразования. Дополнительные сведения о преобразованиях см. в статье [Преобразования](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Указание входных и выходных данных
Целевой объект можно построить инкрементно, если в файле проекта указаны входные и выходные данные.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Указание входных и выходных данных для целевого объекта

- Используйте атрибуты `Inputs` и `Outputs` для элемента `Target`. Например:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] может сравнить метки времени входных файлов с метками времени выходных файлов и определить, следует ли пропустить, построить или частично перестроить целевой объект. В следующем примере, если какой-либо файл в списке элементов `@(CSFile)` новее, чем файл *hello.exe*, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] запустит целевой объект; в противном случае он будет пропущен.

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Когда в целевом объекте указаны входные и выходные данные, все выходные данные можно сопоставить только с одними входными данными, либо между выходными и входными данными может отсутствовать прямое сопоставление. В предыдущей [задаче Csc](../msbuild/csc-task.md), например, выходные данные, *hello.exe*, нельзя сопоставить с отдельными выходными данными — это зависит от всех остальных.

> [!NOTE]
> Для целевого объекта, в котором нет прямого сопоставления между входными и выходными данными, построение всегда будет выполняться чаще, чем для целевого объекта, в котором все выходные данные можно сопоставить только с одними входными данными, поскольку [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] не сможет определить какие выходные данные необходимо перестроить, если изменены некоторые входные данные.

Задачи, в которых можно определить прямое сопоставление между выходными и входными данными, такие как [задача LC](../msbuild/lc-task.md), лучше всего подходят для инкрементных сборок в отличие от таких задач, как [Csc](../msbuild/csc-task.md) и [Vbc](../msbuild/vbc-task.md), в которых из ряда входных данных создается только одна выходная сборка.

## <a name="example"></a>Пример
В следующем примере используется проект, который создает файлы справки для гипотетической справочной системы. В проекте выполняется преобразование исходных *TXT*-файлов в промежуточные *CONTENT*-файлы, которые затем объединяются с XML-файлами метаданных для получения итогового *HELP*-файла, используемого в справке. В проекте используются следующие гипотетические задачи.

- `GenerateContentFiles`: преобразует *TXT*-файлы в *CONTENT*-файлы.

- `BuildHelp`: объединяет *CONTENT*-файлы и XML-файлы метаданных для сборки итогового *HELP*-файла.

В проекте используются преобразования для создания взаимно однозначного сопоставления между входными и выходными данными в задаче `GenerateContentFiles`. Дополнительные сведения см. в статье [Преобразования](../msbuild/msbuild-transforms.md). Кроме того, элемент `Output` настроен на автоматическое использование выходных данных задачи `GenerateContentFiles` в качестве входных данных для задачи `BuildHelp`.

Этот файл проекта содержит оба целевых объекта `Convert` и `Build`. Задачи `GenerateContentFiles` и `BuildHelp` помещаются в целевые объекты `Convert` и `Build` соответственно, чтобы все целевые объекты можно было построить инкрементно. Используя элемент `Output`, выходные данные задачи `GenerateContentFiles` помещаются в список элементов `ContentFile`, где они могут использоваться в качестве входных данных для задачи `BuildHelp`. Использование элемента `Output` таким образом позволяет автоматически представить выходные данные одной задачи в качестве входных данных для другой задачи, что исключает необходимость в перечислении отдельных элементов или списков элементов вручную в каждой задаче.

> [!NOTE]
> Несмотря на то что для целевого объекта `GenerateContentFiles` используется инкрементное построение, все выходные данные этого целевого объекта всегда требуются в качестве входных данных для целевого объекта `BuildHelp`. При использовании элемента `Output` [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] автоматически предоставляет все выходные данные одного целевого объекта в качестве входных данных для другого целевого объекта.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <TXTFile Include="*.txt"/>
        <XMLFiles Include="\metadata\*.xml"/>
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
            MetadataFiles = "@(XMLFiles)"
            OutputFileName = "$(MSBuildProjectName).help"/>
    </Target>
</Project>
```

## <a name="see-also"></a>См. также
- [Целевые объекты](../msbuild/msbuild-targets.md)
- [Элемент Target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Преобразования](../msbuild/msbuild-transforms.md)
- [Задача Csc](../msbuild/csc-task.md)
- [Задача Vbc](../msbuild/vbc-task.md)
