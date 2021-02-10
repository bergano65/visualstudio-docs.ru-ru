---
title: Задача LC | Документация Майкрософт
description: Узнайте, как в MSBuild используется задача LC для создания программы-оболочки для LC.exe, позволяющей создать файл лицензии из LICX-файла.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 881eb0cc8a3c872ed7166f8aff30420730f88c0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913759"
---
# <a name="lc-task"></a>LC - задача

Создает программу-оболочку для файл *LC.exe* для создания *LICENSE*-файла из *LICX*-файла. Дополнительные сведения о *LC.exe* см. в разделе [LC.exe (компилятор лицензий)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры для задачи `LC`.

|Параметр|Описание|
|---------------|-----------------|
|`LicenseTarget`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Определяет исполняемый файл, для которого создаются *LICENSES*-файлы.|
|`NoLogo`|Необязательный параметр `Boolean`.<br /><br /> Отключает отображение эмблемы Майкрософт при запуске.|
|`OutputDirectory`|Необязательный параметр `String`.<br /><br /> Определяет каталог для размещения выходных *LICENSES*-файлов.|
|`OutputLicense`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Определяет имя *LICENSES*-файла. Если имя не указано, используется имя *LICX*-файла, а создаваемый *LICENSES*-файл помещается в каталог, содержащий *LICX*-файл.|
|`ReferencedAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Определяет компоненты, на которые имеются ссылки, для загрузки при создании *LICENSES*-файла.|
|`SdkToolsPath`|Необязательный параметр `String`.<br /><br /> Указывает путь к средствам пакета SDK, например *resgen.exe*.|
|`Sources`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Определяет элементы, содержащие лицензируемые компоненты для включения в *LICENSES*-файл. См. дополнительные сведения см. в документации по параметру `/complist` в [файле LС.exe (компиляторе лицензий)](/dotnet/framework/tools/lc-exe-license-compiler).|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Пример

В следующем примере задача `LC` компилирует лицензии.

```xml
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

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
