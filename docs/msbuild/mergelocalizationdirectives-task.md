---
title: "Задача MergeLocalizationDirectives | Microsoft Docs"
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
  - "локализация XAML [WPF MSBuild], перемещение комментариев и атрибутов в отдельный файл"
  - "MergeLocalizationDirectives - задача [WPF MSBuild]"
  - "MergeLocalizationDirectives - задача [WPF MSBuild], параметры"
  - "перемещение комментариев и атрибутов локализации в отдельный файл [WPF MSBuild]"
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача MergeLocalizationDirectives
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задача <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> объединяет атрибуты локализации и примечания одного или нескольких файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в один файл для всей сборки.  
  
## Параметры задачи  
  
|Параметр|Описание|  
|--------------|--------------|  
|`GeneratedLocalizationFiles`|Обязательный параметр **ITaskItem\[\]**.<br /><br /> Задание списка файлов директив локализации для отдельных файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputFile`|Обязательный выходной параметр типа **String**.<br /><br /> Задание выходного пути для скомпилированной сборки директив локализации.|  
  
## Заметки  
 К содержимому [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] можно добавить атрибуты локализации и примечания.  С поддержкой локализации [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] можно удалить атрибуты локализации и примечания, а также поместить их в файл .loc, расположенный отдельно от созданной сборки.  Это можно сделать с помощью атрибута **LocalizationPropertyStorage**.  Дополнительные сведения об атрибутах локализации, примечаниях и атрибуте **LocalizationPropertyStorage** см. в разделе [Атрибуты и комментарии локализации](../Topic/Localization%20Attributes%20and%20Comments.md).  
  
## Пример  
 В следующем примере атрибуты локализации и примечания нескольких файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] объединяются в один файл .loc.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)