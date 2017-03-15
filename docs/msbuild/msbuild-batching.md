---
title: "Пакетная обработка в MSBuild | Microsoft Docs"
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
  - "MSBuild, пакетная обработка"
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Пакетная обработка в MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] можно разделять списки элементов на разные категории, или пакеты, на основании метаданных элементов и выполнять целевой объект или задачу с использованием каждого пакета в отдельности.  
  
## Пакетная обработка задач  
 Пакетная обработка задач позволяет упростить файлы проекта, предоставляя способ разделения списков элементов на различные пакеты и передачи каждого пакета задаче отдельно.  Это означает, что в файле проекта необходимо только один раз объявить задачу и ее атрибуты, даже если задача выполняется несколько раз.  
  
 Используя запись %\(*ItemMetaDataName*\) в одном из атрибутов задачи, вы указываете, что [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] следует выполнить пакетную обработку задачи.  В приведенном ниже примере список элементов `Example` разделяется на пакеты на основании значения метаданных элемента `Color`, и каждый из пакетов отдельно передается в задачу `MyTask`.  
  
> [!NOTE]
>  Если ссылка на список элементов не используется в каких\-либо других атрибутах задачи, или имя метаданных может оказаться неоднозначным, можно использовать запись %\(*ItemCollection.ItemMetaDataName*\), чтобы полностью определить значение метаданных элемента, которое будет использоваться для пакетной обработки.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Другие характерные примеры пакетной обработки см. в разделе [Метаданные элементов в пакетной обработке задач](../msbuild/item-metadata-in-task-batching.md).  
  
## Пакетная обработка целевых объектов  
 Прежде чем выполнять целевой объект, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] проверяет актуальность входных и выходных данных целевого объекта.  Если и входные, и выходные данные актуальны, целевой объект пропускается.  Если пакетная обработка используется в задаче, находящейся внутри целевого объекта, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] требуется определить, являются ли актуальными входные и выходные данные для каждого пакета элементов.  Иначе целевой объект выполняется каждый раз.  
  
 В следующем примере показан элемент `Target`, содержащий атрибут `Outputs` с записью %\(*ItemMetaDataName*\).  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] разделит список элементов `Example` на пакеты на основании значения метаданных элемента `Color` и проанализирует отметки времени выходных файлов для каждого пакета.  Если выходные данные из пакета неактуальны, целевой объект выполняется.  В противном случае целевой объект пропускается.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Другой пример пакетной обработки целевого объекта см. в разделе [Метаданные элементов в пакетной обработке целевых объектов](../msbuild/item-metadata-in-target-batching.md).  
  
## Функции свойств, использующие метаданные  
 Управлять пакетной обработкой можно с помощью функций свойств, включающих метаданные.  Например:  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 используется функция <xref:System.IO.Path.Combine%2A> для объединения пути к корневой папке с путем к элементу Compile.  
  
 Функции свойств не могут использоваться в значениях метаданных.  Например:  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 не допускается.  
  
 Дополнительные сведения о функциях свойств см. в разделе [Функции свойств](../msbuild/property-functions.md).  
  
## См. также  
 [Элемент ItemMetadata \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [Основные возможности MSBuild](../msbuild/msbuild-concepts.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Дополнительные возможности](../msbuild/msbuild-advanced-concepts.md)