---
title: "Задача MarkupCompilePass2 | Microsoft Docs"
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
  - "MarkupCompilePass2 - задача [WPF MSBuild]"
  - "MarkupCompilePass2 - задача [WPF MSBuild], параметры"
  - "выполнение второго прохода разметки [WPF MSBuild], MarkupCompilePass2 - задача"
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача MarkupCompilePass2
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задача <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> выполняет компиляцию разметки второго прохода на [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] файлах, ссылочные типы которых имеются в том же проекте.  
  
## Параметры задачи  
  
|Параметр|Описание|  
|--------------|--------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Необязательный логический параметр **Boolean**.<br /><br /> Определяет то, выполняется ли задача в отдельном <xref:System.AppDomain>.  Если этот параметр возвращает значение **false**, то задача выполняется в том же самом <xref:System.AppDomain> как и [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)], и выполняется быстрее.  Если этот параметр возвращает значение **true**, то задача выполняется во втором <xref:System.AppDomain>, который изолирован от [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] и работает медленнее.|  
|`AssembliesGeneratedDuringBuild`|Дополнительный параметр **String\[\]**.<br /><br /> Задает ссылки на сборки, которые изменяются в процессе компоновки.  Например, решение [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] может содержать один проект, который ссылается на выходные данные компиляции другого проекта.  В этом случае скомпилированный результат второго проекта можно добавить к **AssembliesGeneratedDuringBuild**.<br /><br /> Примечание: объект **AssembliesGeneratedDuringBuild** должен содержать ссылки на полный комплект, которые созданы в соответствии с решением построения.|  
|`AssemblyName`|Обязательный параметр **String**.<br /><br /> Задает короткое имя сборки, которая создается для проекта.  Например, если проект создает исполняемый файл [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] с именем **WinExeAssembly.exe**, то параметр **AssemblyName** имеет значение **WinExeAssembly**.|  
|`GeneratedBaml`|Необязательный выходной параметр **ITaskItem\[\]**.<br /><br /> Содержит список созданных файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`KnownReferencePaths`|Дополнительный параметр **String\[\]**.<br /><br /> Задает ссылки на сборки, которые никогда не изменяются в процессе компоновки.  Включает сборки, которые находятся в [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], в каталоге установки [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] и т. д.|  
|`Language`|Обязательный параметр **String**.<br /><br /> Задает управляемый язык, который поддерживает компилятор.  Допустимые значения: **C\#**"  **VB**"  **JScript**и  **C\+\+**.|  
|`LocalizationDirectivesToLocFile`|Необязательный параметр **String**.<br /><br /> Определение того, как создать информацию о локализации для каждого исходного файла [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  Разрешенными параметрами являются **None**, **CommentsOnly** и **All**.|  
|`OutputPath`|Обязательный параметр **String**.<br /><br /> Указывает папку, в которой создаются файлы двоичного формата для созданного [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputType`|Обязательный параметр **String**.<br /><br /> Задает тип сборки, которая создается проектом.  Разрешенными параметрами являются **winexe**, **exe**, **library** и **netmodule**.|  
|`References`|Необязательный параметр **ITaskItem\[\]**.<br /><br /> Задает список содержащихся в файлах ссылок на сборки, которые содержат типы, используемые в файлах [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  Одна ссылка это ссылка на сборку, созданную задачей <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, которая должна выполняться перед задачей <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>.|  
|`RootNamespace`|Необязательный параметр **String**.<br /><br /> Задает корневое пространство имен для классов, имеющихся внутри проекта.  **RootNamespace** также используется как пространство имен по умолчанию созданного файла управляемого кода, когда соответствующий файл [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] не включает атрибут `x:Class`.|  
|`XAMLDebuggingInformation`|Необязательный логический параметр **Boolean**.<br /><br /> Когда присвоено значение **true**, создается диагностическая информация, которая включается в откомпилированный [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], чтобы способствовать отладке.|  
  
## Заметки  
 Перед запуском **MarkupCompilePass2** вы должны создать временную сборку, содержащую типы, которые используются файлами [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], чья метка прохода компиляции разметки была отложена.  Временная сборка создается запуском задачи **GenerateTemporaryTargetAssembly**.  
  
 Ссылка на созданную временную сборку передается файлам <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>, когда они выполняются, позволяя файлам [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], компиляция которых была отложена при первом проходе процесса компиляции, быть скомпилированными в двоичный формат.  
  
## Пример  
 Следующий пример показывает, как использовать задачу <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> для выполнения второго прохода компиляции.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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