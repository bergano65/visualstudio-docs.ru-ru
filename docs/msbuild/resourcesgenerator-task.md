---
title: "Задача ResourcesGenerator | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "внедрение ресурсов в RESOURCES-файл [WPF MSBuild]"
  - "ResourcesGenerator - задача [WPF MSBuild]"
  - "ResourcesGenerator - задача [WPF MSBuild], параметры"
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача ResourcesGenerator
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задача <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> внедряет один или несколько ресурсов \(JPG\-, ICO\-, BMP\-файлов, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в двоичном формате и других\) в RESOURCES\-файл.  
  
## Параметры задачи  
  
|Параметр|Описание|  
|--------------|--------------|  
|`OutputPath`|Обязательный параметр **String**.<br /><br /> Задает путь к выходному каталогу.  Если путь не является абсолютным, он трактуется как заданный относительно корневого каталога проекта.|  
|`OutputResourcesFile`|Обязательный выходной параметр **ITaskItem\[\]**.<br /><br /> Задает путь и имя генерируемого RESOURCES\-файла.  Если путь не является абсолютным, местоположение генерируемого RESOURCES\-файла задается относительно корневого каталога проекта.|  
|`ResourcesFiles`|Обязательный параметр **ITaskItem\[\]**.<br /><br /> Задает один или несколько ресурсов для внедрения в генерируемый RESOURCES\-файл.|  
  
## Пример  
 В следующем примере генерируется RESOURCES\-файл с одним ресурсом в формате BMP.  BMP\-ресурс генерируется в каталоге, заданном относительно корневого каталога проекта.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)