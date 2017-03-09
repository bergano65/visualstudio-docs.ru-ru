---
title: "Задача AspNetCompiler | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AspNetCompiler - задача [MSBuild]"
  - "MSBuild, AspNetCompiler - задача"
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача AspNetCompiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задача `AspNetCompiler` представляет собой оболочку для aspnet\_compiler.exe – программы предварительной компиляции приложений [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
## Параметры задачи  
 В следующей таблице описаны параметры задачи `AspNetCompiler`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`AllowPartiallyTrustedCallers`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, для строго именованных сборок будут разрешены частично доверенные вызывающие объекты.|  
|`Clean`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, будет произведена чистая сборка предварительно скомпилированного приложения.  Все ранее скомпилированные приложения будут перекомпилированы.  Значение по умолчанию — `false`.  Этот параметр соответствует переключателю **\-c** программы aspnet\_compiler.exe.|  
|`Debug`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, во время компиляции выводится отладочная информация \(PDB\-файл\).  Значение по умолчанию — `false`.  Этот параметр соответствует переключателю **\-d** программы aspnet\_compiler.exe.|  
|`DelaySign`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, сборка не подписывается полностью при создании.|  
|`FixedNames`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, скомпилированным сборкам будут даваться фиксированные имена.|  
|`Force`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, задача перезаписывает существующий целевой каталог.  Текущее содержимое каталога теряется.  Значение по умолчанию — `false`.  Этот параметр соответствует переключателю **\-f** программы aspnet\_compiler.exe.|  
|`KeyContainer`|Необязательный параметр типа `String`.<br /><br /> Задает контейнер ключа строго имени.|  
|`KeyFile`|Необязательный параметр типа `String`.<br /><br /> Задает физический путь к файлу ключей строгого имени.|  
|`MetabasePath`|Необязательный параметр типа `String`.<br /><br /> Задает полный путь к метабазе IIS приложения.  Данный параметр несовместим с параметрами `VirtualPath` или `PhysicalPath`.  Этот параметр соответствует переключателю **\-m** программы aspnet\_compiler.exe.|  
|`PhysicalPath`|Необязательный параметр типа `String`.<br /><br /> Задает физический путь к компилируемому приложению.  Если данный параметр отсутствует, для поиска приложения используется метабаза IIS.  Этот параметр соответствует переключателю **\-p** программы aspnet\_compiler.exe.|  
|`TargetFrameworkMoniker`|Необязательный параметр типа `String`.<br /><br /> задает моникер целевой платформы, указывающий, какую версию .NET Framework файла aspnet\_compiler.exe нужно использовать.  Принимает только специальные имена .NET Framework.|  
|`TargetPath`|Необязательный параметр типа `String`.<br /><br /> Задает физический путь для размещения скомпилированного приложения.  Если этот параметр не указан, приложение предварительно компилируется на месте.|  
|`Updateable`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, предварительно скомпилированное приложение будет обновляемым.  Значение по умолчанию — `false`.  Этот параметр соответствует переключателю **\-u** программы aspnet\_compiler.exe.|  
|`VirtualPath`|Необязательный параметр типа `String`.<br /><br /> Виртуальный путь к компилируемому приложению.  Если задан параметр `PhysicalPath`, для поиска приложения используется физический путь.  В противном случае используется метабаза IIS, и предполагается, что приложение находится на узле по умолчанию.  Этот параметр соответствует переключателю **\-v** программы aspnet\_compiler.exe.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.ToolTask>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## Пример  
 В следующем примере кода задача `AspNetCompiler` используется для предварительной компиляции приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)