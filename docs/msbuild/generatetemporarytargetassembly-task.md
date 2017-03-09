---
title: "Задача GenerateTemporaryTargetAssembly | Microsoft Docs"
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
  - "процесс построения [WPF MSBuild], страница XAML относится к типу, объявленному локально"
  - "создание сборки [WPF MSBuild], страница XAML относится к типу, объявленному локально"
  - "GenerateTemporaryTargetAssembly - задача [WPF MSBuild]"
  - "GenerateTemporaryTargetAssembly - задача [WPF MSBuild], параметры"
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача GenerateTemporaryTargetAssembly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задача <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> создает сборку, если хотя бы одна страница [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] в проекте ссылается на тип, объявленный в этом проекте локально.  Созданная сборка удаляется после завершения или сбоя процесса построения.  
  
## Параметры задачи  
  
|Параметр|Описание|  
|--------------|--------------|  
|`AssemblyName`|Обязательный параметр **String**.<br /><br /> Задание короткого имени сборки, созданной для проекта, которое также является именем временно создаваемой конечной сборки.  Например, если проект создает исполняемый файл [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] с именем **WinExeAssembly.exe**, то параметр **AssemblyName** имеет значение **WinExeAssembly**.|  
|`CompileTargetName`|Обязательный параметр **String**.<br /><br /> Указание имени целевого объекта [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)], используемого для создания сборок из файлов исходного кода.  **CompileTargetName** обычно имеет значение **CoreCompile**.|  
|`CompileTypeName`|Обязательный параметр **String**.<br /><br /> Указание типа компиляции, выполняемой целевым объектом, заданным с помощью параметра **CompileTargetName**.  Для целевого объекта **CoreCompile** используется значение **Compile**.|  
|`CurrentProject`|Обязательный параметр **String**.<br /><br /> Указание полного пути к файлу проекта [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] для проекта, которому требуется создание временной конечной сборки.|  
|`GeneratedCodeFiles`|Необязательный параметр **ITaskItem\[\]**.<br /><br /> Задание списка файлов управляемого кода для конкретного языка, созданных задачей [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md).|  
|`IntermediateOutputPath`|Обязательный параметр **String**.<br /><br /> Задание каталога, в котором создается временная конечная сборка.|  
|`MSBuildBinPath`|Обязательный параметр **String**.<br /><br /> Указание расположения файла **MSBuild.exe**, необходимого для компиляции временной конечной сборки.|  
|`ReferencePath`|Необязательный параметр **ITaskItem\[\]**.<br /><br /> Задание списка сборок с указанием пути и имени файла, на которые ссылаются типы, скомпилированные во временную конечную сборку.|  
|`ReferencePathTypeName`|Обязательный параметр **String**.<br /><br /> Указание параметра, используемого параметром целевого объекта компиляции \(**CompileTargetName**\), который задает список ссылок на сборку \(**ReferencePath**\).  Допустимым значением является **ReferencePath**.|  
  
## Заметки  
 Во время первого прохода компиляции разметки, запущенного задачей [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] компилируются в двоичный формат.  Следовательно, компилятору необходим список сборок, на которые имеются ссылки и которые содержат типы, используемые файлами [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  Однако, если файл [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] использует тип, заданный в том же проекте, соответствующая сборка для этого проекта не создается до построения проекта.  Таким образом, ссылку на сборку нельзя предоставить во время первого прохода компиляции разметки.  
  
 Вместо этого задача **MarkupCompilePass1** откладывает преобразование файлов [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], содержащих ссылки на типы того же проекта, до второго прохода компиляции разметки, который выполняется задачей [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  Перед выполнением задачи **MarkupCompilePass2** создается временная сборка.  Эта сборка содержит типы, которые используются файлами [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], для которых был отложен проход компиляции разметки.  Ссылка на созданную сборку передается задаче **MarkupCompilePass2**, когда она выполняется, позволяя файлам [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], компиляция которых была отложена, быть скомпилированными в двоичный формат.  
  
## Пример  
 В следующем примере создается временная сборка, так как `Page1.xaml` содержит ссылку на тип, заданный в том же проекте.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GenerateTemporaryTargetAssemblyTask">  
    <GenerateTemporaryTargetAssembly  
      AssemblyName="WPFMSBuildSample"  
      CompileTargetName="CoreCompile"  
      CompileTypeName="Compile"  
      CurrentProject="FullBuild.proj"  
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"  
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"  
      IntermediateOutputPath=".\obj\debug\"  
      MSBuildBinPath="$(MSBuildBinPath)"  
      ReferencePathTypeName="ReferencePath"/>  
  </Target>  
</Project>  
```  
  
## См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Общие сведения о приложениях браузера WPF XAML](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)