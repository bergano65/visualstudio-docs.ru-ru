---
title: "Задача GetWinFXPath | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "получение каталога текущей среды выполнения .NET Framework [WPF MSBuild]"
  - "GetWinFXPath - задача [WPF MSBuild]"
  - "GetWinFXPath - задача [WPF MSBuild], параметры"
  - "получение пути к текущей среде выполнения .NET Framework [WPF MSBuild]"
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача GetWinFXPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задача <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> возвращает папку текущего времени выполнения [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)].  
  
## Параметры задачи  
  
|Параметр|Описание|  
|--------------|--------------|  
|`WinFXPath`|Необязательный выходной параметр **String**.<br /><br /> Действительный путь для времени выполнения [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)].|  
|`WinFXNativePath`|Обязательный параметр **String**.<br /><br /> Путь для собственного времени выполнения [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)].|  
|`WinFXWowPath`|Обязательный параметр **String**.<br /><br /> Путь к сборкам [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] в 32\-разрядном модуле **Windows on Windows** внутри 64\-разрядных систем.|  
  
## Заметки  
 Если задача <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> выполняется на 64\-разрядном процессоре, то параметру **WinFXPath** назначается путь, хранящийся в параметре **WinFXWowPath**; в противном случае параметру **WinFXPath** назначается путь, хранящийся в параметре **WinFXNativePath**.  
  
## Пример  
 В следующем примере показано, как с помощью задачи **GetWinFXPath** обнаружить собственный путь для времени выполнения [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)].  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)