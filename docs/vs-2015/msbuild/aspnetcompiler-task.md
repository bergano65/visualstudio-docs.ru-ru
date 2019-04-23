---
title: Задача AspNetCompiler | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1267ddbb093f59eaa60fae0eef2d83f6b7ba2e24
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654009"
---
# <a name="aspnetcompiler-task"></a>Задача AspNetCompiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задача `AspNetCompiler` создает оболочку для служебной программы aspnet_compiler.exe, которая выполняет предварительную компиляцию приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `AspNetCompiler`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр имеет значение `true`, сборка со строгим именем допускает вызовы с частичным доверием.|  
|`Clean`|Необязательный параметр `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, то для предварительно скомпилированного приложения будет выполнена чистая сборка. Все ранее скомпилированные компоненты будут перекомпилированы. Значение по умолчанию — `false`. Этот параметр соответствует параметру командной строки **-c** для Aspnet_compiler.exe.|  
|`Debug`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр имеет значение `true`, то во время компиляции создается отладочная информация (PDB-файл). Значение по умолчанию — `false`. Этот параметр соответствует параметру командной строки **-d** для Aspnet_compiler.exe.|  
|`DelaySign`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр имеет значение `true`, сборка не подписывается полностью при создании.|  
|`FixedNames`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр имеет значение `true`, скомпилированным сборкам будут присвоены фиксированные имена.|  
|`Force`|Необязательный параметр `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, задача перезаписывает конечный каталог, если он уже существует. Все содержимое каталога будет утеряно. Значение по умолчанию — `false`. Этот параметр соответствует параметру командной строки **-f** для aspnet_compiler.exe.|  
|`KeyContainer`|Необязательный параметр `String` .<br /><br /> Задает контейнер ключа для строгого имени.|  
|`KeyFile`|Необязательный параметр `String` .<br /><br /> Указывает физический путь к файлу ключа для строгого имени.|  
|`MetabasePath`|Необязательный параметр `String` .<br /><br /> Указывает полный путь к метабазе IIS приложения. Этот параметр нельзя использовать вместе с параметром `VirtualPath` или `PhysicalPath`. Этот параметр соответствует параметру командной строки **-m** для aspnet_compiler.exe.|  
|`PhysicalPath`|Необязательный параметр `String` .<br /><br /> Указывает физический путь к компилируемому приложению. Если этот параметр отсутствует, для поиска приложения используется метабаза IIS. Этот параметр соответствует параметру командной строки **-p** для aspnet_compiler.exe.|  
|`TargetFrameworkMoniker`|Необязательный параметр `String` .<br /><br /> Задает параметр TargetFrameworkMoniker, который определяет используемую версию .NET Framework для aspnet_compiler.exe. Принимает только моникеры платформы .NET Framework.|  
|`TargetPath`|Необязательный параметр `String` .<br /><br /> Указывает физический путь, по которому компилируется приложение. Если этот параметр не указан, приложение предкомпилируется на месте.|  
|`Updateable`|Необязательный параметр `Boolean` .<br /><br /> Если этот параметр имеет значение `true`, то предкомпилированное приложения будет обновляемым.  Значение по умолчанию — `false`. Этот параметр соответствует параметру командной строки **-u** для aspnet_compiler.exe.|  
|`VirtualPath`|Необязательный параметр `String` .<br /><br /> Виртуальный путь к компилируемому приложению. Если указан параметр `PhysicalPath`, для поиска приложения используется физический путь. В противном случае используется метабаза IIS, и предполагается, что приложение расположено в узле по умолчанию. Этот параметр соответствует параметру командной строки **-v** для aspnet_compiler.exe.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.ToolTask>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода задача `AspNetCompiler` выполняет предварительную компиляцию приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
