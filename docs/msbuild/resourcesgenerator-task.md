---
title: "Задача ResourcesGenerator | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: aed4b108ad10272579ee5acd43128311003e9ea3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="resourcesgenerator-task"></a>Задача ResourcesGenerator
Задача <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> внедряет один или несколько ресурсов (файлов JPG, ICO, BMP, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в двоичном формате и других) в RESOURCES-файл.  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`OutputPath`|Обязательный параметр **string**.<br /><br /> Определяет абсолютный путь выходного каталога. Если путь не является абсолютным, он интерпретируется относительно корневого каталога проекта.|  
|`OutputResourcesFile`|Обязательный параметр вывода **ITaskItem[]**.<br /><br /> Определяет путь и имя для созданного RESOURCES-файла. Если путь не является абсолютным, RESOURCES-файл интерпретируется относительно корневого каталога проекта.|  
|`ResourcesFiles`|Обязательный параметр **ITaskItem[]**.<br /><br /> Определяет один или несколько ресурсов для внедрения в создаваемый RESOURCES-файл.|  
  
## <a name="example"></a>Пример  
 Следующий пример создает RESOURCES-файл с одним BMP-ресурсом. BMP-ресурс создается в каталоге, который интерпретируется относительно корневого каталога проекта.  
  
```xml  
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
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)