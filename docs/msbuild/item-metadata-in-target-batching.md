---
title: "Метаданные элементов в пакетной обработке целевых объектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пакетная обработка [MSBuild]"
  - "MSBuild, пакетная обработка целевых объектов"
  - "пакетная обработка целевых объектов [MSBuild]"
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Метаданные элементов в пакетной обработке целевых объектов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] можно выполнить анализ зависимости входных и выходных данных целевого объекта построения.  Если обнаружено, что входные и выходные данные целевого объекта актуальны, этот целевой объект пропускается, а построение продолжается.  Для указания элементов, которые нужно проверять во время анализа зависимости, в элементах `Target` используются атрибуты `Inputs` и `Outputs`.  
  
 Если в целевом объекте содержится задача, в которой в качестве входных и выходных данных используются пакетные элементы, элементу `Target` целевого объекта следует использовать пакетную обработку в атрибуте `Inputs` или `Outputs`, чтобы позволить [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] пропустить пакеты элементов, которые уже актуальны.  
  
## Целевые объекты при пакетной обработке  
 В приведенном ниже примере кода содержится список элементов с именем `Res`, который делится на два пакета на основании метаданных элемента `Culture`.  Каждый из пакетов передается в задачу `AL`, на выходе которой создается сборка для каждого пакета.  Используя пакетную обработку в атрибуте `Outputs` элемента `Target`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] может определить актуальность каждого отдельного пакета перед выполнением целевого объекта.  Без использования пакетной обработки целевого объекта оба пакета элементов будут выполняться задачей при каждом выполнении целевого объекта.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## См. также  
 [Практическое руководство. Инкрементное построение](../msbuild/how-to-build-incrementally.md)   
 [Пакетная обработка](../msbuild/msbuild-batching.md)   
 [Элемент Target \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Метаданные элементов в пакетной обработке задач](../msbuild/item-metadata-in-task-batching.md)