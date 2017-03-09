---
title: "Задача LC | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#LC"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "LC - задача [MSBuild]"
  - "MSBuild, LC - задача"
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача LC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Служит оболочкой для программы LC.exe, генерирующей LICENSE\-файл из LICX\-файла.  Дополнительные сведения о программе LC.exe см. в разделе [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).  
  
## Параметры  
 В следующей таблице описаны параметры задачи `LC`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`LicenseTarget`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает исполняемый файл, для которого создаются LICENSES\-файлы.|  
|`NoLogo`|Необязательный параметр типа `Boolean`.<br /><br /> Отключает отображение эмблемы Майкрософт при запуске.|  
|`OutputDirectory`|Необязательный параметр типа `String`.<br /><br /> Задает каталог, в котором следует разместить полученные LICENSES\-файлы.|  
|`OutputLicense`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает имя LICENSES\-файла.  Если имя не указано, то используется имя соответствующего LICX\-файла, а создаваемый LICENSES\-файл помещается в каталог, содержащий LICX\-файл.|  
|`ReferencedAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает компоненты, на которые имеются ссылки, подлежащие загрузке при генерации LICENSE\-файла.|  
|`SdkToolsPath`|Необязательный параметр типа `String`.<br /><br /> Задает путь к средствам SDK, таким как resgen.exe.|  
|`Sources`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает элементы, содержащие лицензируемые компоненты, которые подлежат включению в LICENSES\-файл.  Для получения дополнительных сведений см. документацию на переключатель `/complist` в разделе [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).|  
  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.ToolTask>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## Пример  
 В следующем примере задача `LC` используется для компиляции лицензий.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)