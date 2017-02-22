---
title: "Задача BscMake | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.bscmake"
  - "VC.Project.VCBscMakeTool.PreserveSBR"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "BscMake - задача (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), задачи"
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача BscMake
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  BSCMAKE больше не используется в интегрированной среде разработки Visual Studio.  Начиная с Visual Studio 2008, сведения о просмотре автоматически сохраняются в SDF\-файле в папке решения.  
  
 Заключает в оболочку средство «Программа управления сведениями о просмотре Майкрософт» \(bscmake.exe\).  Средство bscmake.exe создает файл сведений о просмотре \(BSC\-файл\) из исходных файлов браузера \(SBR\-файлов\), созданных во время компиляции.  Используйте **браузер объектов** для просмотра BSC\-файла.  Дополнительные сведения см. в разделе [Справочник ВSCMAKE](/visual-cpp/build/reference/bscmake-reference).  
  
## Параметры  
 В следующей таблице описываются параметры задачи **BscMake** .  Большинство параметров задач соответствуют параметрам командной строки.  
  
|Параметр|Описание|  
|--------------|--------------|  
|**AdditionalOptions**|Необязательный параметр **String**.<br /><br /> Список параметров, как указано в командной строке.  Например, «\/*параметр1* \/*параметр2* \/*параметр\#*».  Этот параметр используется для указания параметров, не представленных каким\-либо другим параметром задачи **BscMake**.<br /><br /> Дополнительные сведения см. в разделе [Параметры BSCMAKE](/visual-cpp/build/reference/bscmake-options).|  
|**OutputFile**|Необязательный параметр **String**.<br /><br /> Задает имя файла, которое переопределяет имя выходного файла по умолчанию.<br /><br /> Дополнительные сведения см. в описании параметра **\/o** в разделе [Параметры BSCMAKE](/visual-cpp/build/reference/bscmake-options).|  
|**PreserveSBR**|Необязательный параметр **Boolean**.<br /><br /> Если задано значение `true`, выполняется недобавочная сборка.  Полная недобавочная сборка происходит независимо от того, существует ли BSC\-файл, и предотвращает усечение SBR\-файлов.<br /><br /> Дополнительные сведения см. в описании параметра **\/n** в разделе [Параметры BSCMAKE](/visual-cpp/build/reference/bscmake-options).|  
|**Sources**|Необязательный параметр **ITaskItem\[\]**.<br /><br /> Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.|  
|**SuppressStartupBanner**|Необязательный параметр **Boolean**.<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **\/NOLOGO** в разделе [Параметры BSCMAKE](/visual-cpp/build/reference/bscmake-options).|  
|**TrackerLogDirectory**|Необязательный параметр **String**.<br /><br /> Задает каталог для журнала отслеживания.|  
  
## Заметки  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)