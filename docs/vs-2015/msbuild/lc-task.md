---
title: Задача LC | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ec788e9f0ef80a1543aa15f4ff9bfb21daac6123
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803473"
---
# <a name="lc-task"></a>Задача LC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Создает программу-оболочку для файл LC.exe для создания LICENSE-файла из LICX-файла. См. дополнительные сведения о [LC.exe (компиляторе лицензий)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры для задачи `LC`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`LicenseTarget`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Определяет исполняемый файл, для которого создаются LICENSES-файлы.|  
|`NoLogo`|Необязательный параметр `Boolean` .<br /><br /> Отключает отображение эмблемы Майкрософт при запуске.|  
|`OutputDirectory`|Необязательный параметр `String` .<br /><br /> Определяет каталог для размещения выходных LICENSES-файлы.|  
|`OutputLicense`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Определяет имя LICENSES-файла. Если имя не указано, используется имя LICX-файла, а создаваемый LICENSES-файл помещается в каталог, содержащий LICX-файл.|  
|`ReferencedAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет компоненты, на которые имеются ссылки, для загрузки при создании LICENSES-файла.|  
|`SdkToolsPath`|Необязательный параметр `String` .<br /><br /> Указывает путь к средствам пакета SDK, например resgen.exe.|  
|`Sources`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Определяет элементы, содержащие лицензируемые компоненты для включения в LICENSES-файл. См. дополнительные сведения см. в документации по параметру `/complist` в [файле LС.exe (компиляторе лицензий)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460).|  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.ToolTask>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере задача `LC` компилирует лицензии.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
