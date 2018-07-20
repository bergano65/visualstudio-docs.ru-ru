---
title: Настроить отладку и выпуск конфигураций | Документация Майкрософт
ms.custom: ''
ms.date: 04/10/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea27fdccaadc70f22d9c9c02d75ddef98a11be13
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153102"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Настроить отладку и выпуск конфигураций в Visual Studio
Проекты Visual Studio имеют отдельные конфигурации выпуска и отладки для вашей программы. Как следует из самих названий, производится построение отладочной версии для отладки и версии выпуска для окончательного выпуска программы.  
  
Отладочная конфигурация программы компилируется с полной символической отладочной информацией и без оптимизации. Оптимизация усложняет отладку, поскольку усложняется связь между исходным кодом и сгенерированными инструкциями.  
  
Конфигурация выпуска для программы полностью оптимизируется и не содержит символической отладочной информации. Отладка информация может быть создана в PDB-файлы, [в зависимости от параметров компилятора](#BKMK_symbols_release) , которые используются. Создание PDB-файлы могут быть очень полезно, если позднее возникнет необходимость в отладке версии выпуска.  
  
Дополнительные сведения о конфигурациях сборки см. в разделе [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).  
  
Можно изменить конфигурацию сборки из **построения** меню на панели инструментов или на страницах свойств проекта. Страницы свойств проекта зависят от конкретного языка. Следующая процедура показывает, как изменить конфигурацию сборки из меню и на панели инструментов. Дополнительные сведения о том, как изменить конфигурацию построения в проектах на разных языках, см. в подразделе ниже.  
  
## <a name="change-the-build-configuration"></a>Измените конфигурацию сборки  
  
1.  Из **построения** меню, выберите **Configuration Manager**, а затем выберите **Отладка** или **выпуска**.  
  
2.  На панели инструментов выберите либо **Отладка** или **выпуска** из **конфигураций решения** поле со списком.  
  
     ![Конфигурация построения панели инструментов](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Эта панель инструментов недоступна в выпусках Express. Можно использовать **собрать решение F6** и **начать отладку F5** пунктов меню для выбора конфигурации.

## <a name="BKMK_symbols_release"></a>Создание файлов символов (.pdb) для сборки

Для большинства типов проектов PDB-файлы создаются по умолчанию для обоих отладочные и выпускные построения, но параметры по умолчанию различаются в зависимости от типа конкретного проекта и версии Visual Studio. Можно настроить ли компилятор создает PDB-файлы и какого рода отладочную информацию для включения.

> [!IMPORTANT] 
> Отладчик загружает PDB-файл для исполняемого файла, только если он точно соответствует PDB-файлу, который был создан при сборке исполняемого файла (то есть это должен быть либо оригинальный PDB-файл, либо его копия). Дополнительные сведения см. в статье [Why does Visual Studio require debugger symbol files to exactly match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Каждый тип проекта может иметь другим способом настройки этих параметров.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Создать файлы символов для проекта C#, ASP.NET или Visual Basic

Подробные сведения о параметрах проекта для конфигураций отладки C# см. в разделе [параметры для конфигурации отладки C# проекта](../debugger/project-settings-for-csharp-debug-configurations.md). Visual Basic, см. в разделе [в этом разделе](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Щелкните правой кнопкой мыши проект в обозревателе решений и выберите **свойства**.

2. Выберите **выпуска** или **Отладка** строится на основе **конфигурации** списка.

2. Выберите **построения** параметры и нажмите кнопку **Дополнительно** кнопки.

    В Visual Basic, выберите **компиляции** параметры и **Дополнительные параметры компиляции** вместо кнопки.

3. Выберите **полный**, **переносимой**, или **pdb_only** в **отладочную информацию** поле со списком (**создать отладочную информацию** в Visual Basic).

    Переносимый формат является самой последней кросс платформенных для .NET Core. Дополнительные сведения о параметрах см. в разделе [диалоговое окно Дополнительные параметры построения (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

    ![Создать файл PDB для сборок в C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. Построить проект.

    Файлы символов создаются в той же папке, как исполняемый файл или основного выходного файла.

### <a name="generate-symbol-files-for-a-c-project"></a>Создать файлы символов для проекта C++

1. Щелкните правой кнопкой мыши проект в обозревателе решений и выберите **свойства**.

2. Выберите **выпуска** или **Отладка** строится на основе **конфигурации** списка.

2. В разделе **компоновщика > Отладка**, выберите требуемого параметры **создать отладочную информацию**.

    Подробные сведения о параметрах проекта для конфигураций отладки в C++ см. в разделе [параметры для конфигурации отладки C++ проекта](../debugger/project-settings-for-a-cpp-debug-configuration.md).

4. Настройка параметров для создания файлов базы данных программы

    В большинстве проектов C++, значение по умолчанию — `$(OutDir)$(TargetName).pdb`, который создает PDB-файлы в выходную папку.

    ![Создать файл PDB для сборок в C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. Построить проект.

    Файлы символов создаются в той же папке, как исполняемый файл или основного выходного файла.
  
## <a name="see-also"></a>См. также  
 [Указание файлов символов (.pdb) и исходных файлов в отладчике излюбленной Studio](../debugger/debugger-settings-and-preparation.md)  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md)
