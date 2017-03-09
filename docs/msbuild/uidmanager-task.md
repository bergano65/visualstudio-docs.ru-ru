---
title: "Задача UidManager | Microsoft Docs"
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
  - "проверка UID при локализации элементов XAML [WPF MSBuild]"
  - "локализация элементов XAML [WPF MSBuild], управление UID"
  - "управление UID при локализации элементов XAML [WPF MSBuild]"
  - "UidManager - задача [WPF MSBuild]"
  - "UidManager - задача [WPF MSBuild], параметры"
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача UidManager
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задача <xref:Microsoft.Build.Tasks.Windows.UidManager> проверяет, обновляет или удаляет уникальные идентификаторы \(UID\) для локализации всех элементов [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)], содержащихся в исходных файлах [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  
  
## Параметры задачи  
  
|Параметр|Описание|  
|--------------|--------------|  
|`IntermediateDirectory`|Необязательный параметр **String**.<br /><br /> Указывает каталог, используемый для создания резервной копии исходных файлов [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], заданных параметром **MarkupFiles**.|  
|`MarkupFiles`|Обязательный параметр **ITaskItem\[\]**.<br /><br /> Указывает исходные файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], включаемые в процессы проверки UID, обновления и удаления.|  
|`Task`|Обязательный параметр **String**.<br /><br /> Указывает задачу управления UID, которую требуется выполнить.  Допустимыми параметрами являются **Check**, **Update** или **Remove**.|  
  
## Пример  
 В следующем примере для проверки указанных исходных файлов [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], содержащих элементы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] с соответствующими UID, используется задача <xref:Microsoft.Build.Tasks.Windows.UidManager>.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Практическое руководство. Локализация приложения](../Topic/How%20to:%20Localize%20an%20Application.md)