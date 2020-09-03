---
title: Параллельная сборка нескольких проектов с помощью MSBuild | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f80f0898167de133d78d27d26f97d0ab8ced0b31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75843954"
---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>Параллельное построение нескольких проектов с помощью MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью MSBuild вы можете ускорить сборку нескольких проектов, выполняя ее параллельно. Для параллельного выполнения сборки используйте следующие параметры на компьютере с несколькими процессорами или многоядерным процессором:  
  
- параметр `/maxcpucount` в командной строке;  
  
- Параметр задачи <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> в задаче MSBuild.  
  
> [!NOTE]
> Параметр **/verbosity** (**/v**) в командной строке может также влиять на производительность сборки. Производительность сборки снижается, если установлен "подробный" или "диагностический" уровень детализации журнала сборки (обычно используются для устранения неполадок). Дополнительные сведения см. в разделе [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md) и [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="maxcpucount-switch"></a>Ключ /maxcpucount  
 Если вы используете параметр `/maxcpucount` (или его короткую версию `/m`), MSBuild может создать заданное число процессов MSBuild.exe, которые будут выполняться параллельно. Эти процессы называются рабочими процессами. Каждый рабочий процесс использует отдельное ядро или процессор, если они доступны, и выполняет сборку проекта. Параллельно с этим другие доступные процессоры работают над другими проектами. Например, если для этого параметра задано значение 4, MSBuild создаст четыре рабочих процесса для сборки проекта.  
  
 Если параметр `/maxcpucount` включается в командную строку без указания значения, MSBuild использует значение, соответствующее числу процессоров в компьютере.  
  
 Дополнительные сведения об этом параметре, который появился в MSBuild 3,5, см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
 Следующий пример сообщает MSBuild, что нужно использовать три рабочих процесса. С этой конфигурацией MSBuild сможет одновременно выполнять сборку трех проектов.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## <a name="buildinparallel-task-parameter"></a>Параметр задачи BuildInParallel  
 `BuildInParallel` является необязательным логическим параметром задачи [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Если для `BuildInParallel` установлено значение `true` (значение по умолчанию), создается несколько рабочих процессов для одновременной сборки максимально возможного числа проектов. Для надлежащего выполнения параметр `/maxcpucount` должен иметь значение больше 1, а компьютер должен быть оснащен по меньшей мере двухъядерным процессором или минимум двумя процессорами.  
  
 Следующий пример (отсюда — microsoft.common.targets) демонстрирует использование параметра `BuildInParallel`.  
  
```  
<PropertyGroup>  
    <BuildInParallel Condition="'$(BuildInParallel)' ==   
        ''">true</BuildInParallel>  
</PropertyGroup>  
<MSBuild  
    Projects="@(_MSBuildProjectReferenceExistent)"  
    Targets="GetTargetPath"  
    BuildInParallel="$(BuildInParallel)"  
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);   
        %(_MSBuildProjectReferenceExistent.SetPlatform)"  
    Condition="'@(NonVCProjectReference)'!='' and   
        ('$(BuildingSolutionFile)' == 'true' or   
        '$(BuildingInsideVisualStudio)' == 'true' or   
        '$(BuildProjectReferences)' != 'true') and     
        '@(_MSBuildProjectReferenceExistent)' != ''"  
    ContinueOnError="!$(BuildingProject)">  
    <Output TaskParameter="TargetOutputs"   
        ItemName="_ResolvedProjectReferencePaths"/>  
</MSBuild>  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование нескольких процессоров для построения проектов](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Написание средств ведения журнала с поддержкой нескольких процессоров](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Блог о настройке параллелизма сборки C++](https://blogs.msdn.com/b/visualstudio/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx)
