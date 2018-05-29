---
title: 'Как: настроить отладку и выпуск конфигураций | Документы Microsoft'
ms.custom: H1HackMay2017
ms.date: 04/10/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
ms.openlocfilehash: 8e2eb30d50be7348802518b7cc1b945aa88a26bd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-set-debug-and-release-configurations-in-visual-studio"></a>Как: настроить отладку и выпуск конфигураций, в Visual Studio
Проекты Visual Studio имеют отдельные конфигурации выпуска и отладки для вашей программы. Как следует из самих названий, производится построение отладочной версии для отладки и версии выпуска для окончательного выпуска программы.  
  
Отладочная конфигурация программы компилируется с полной символической отладочной информацией и без оптимизации. Оптимизация усложняет отладку, поскольку усложняется связь между исходным кодом и сгенерированными инструкциями.  
  
Конфигурация выпуска для программы полностью оптимизируется и не содержит символической отладочной информации. Отладка информация может быть создана в PDB-файлы, [в зависимости от параметров компилятора](#BKMK_symbols_release) , которые используются. Создание PDB-файлы могут быть очень полезным, если позднее возникнет необходимость в отладке версии выпуска.  
  
Дополнительные сведения о конфигурациях сборки см. в разделе [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).  
  
Можно изменить конфигурацию сборки из **построения** меню на панели инструментов или на страницах свойств проекта. Страницы свойств проекта зависят от конкретного языка. Следующая процедура показывает, как изменить конфигурацию сборки из меню и на панели инструментов. Дополнительные сведения о том, как изменить конфигурацию построения в проектах на разных языках, см. в подразделе ниже.  
  
## <a name="change-the-build-configuration"></a>Измените конфигурацию сборки  
  
1.  Из **построения** последовательно выберите пункты **Configuration Manager**, а затем выберите **отладки** или **выпуска**.  
  
2.  На панели инструментов выберите **отладки** или **выпуска** из **конфигурации решения** списка.  
  
     ![конфигурации построения инструментов](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Эта панель инструментов недоступна в выпусках Express. Можно использовать **собрать решение F6** и **начать отладку F5** пункты меню для выбора конфигурации.

## <a name="BKMK_symbols_release"></a>Создание файлов символов (.pdb) для построения

Для большинства типов проектов PDB-файлы создаются по умолчанию для обоих отладочные и выпускные построения, но настройки по умолчанию различаются в зависимости от вашего проекта определенного типа и версии Visual Studio. Можно настроить ли компилятор создает PDB-файлы и какого рода сведения об отладке для включения.

> [!IMPORTANT] 
> Отладчик загружает PDB-файл для исполняемого файла, только если он точно соответствует PDB-файлу, который был создан при сборке исполняемого файла (то есть это должен быть либо оригинальный PDB-файл, либо его копия). Дополнительные сведения см. в статье [Why does Visual Studio require debugger symbol files to exactly match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Каждый тип проекта может иметь другим способом настройки этих параметров.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Создавать файлы символов для проекта C# ASP.NET и Visual Basic

Подробные сведения о параметры проекта для конфигурации отладки в C# см. в разделе [параметры для конфигурации отладки C# проекта](../debugger/project-settings-for-csharp-debug-configurations.md). Visual Basic. в разделе [в этом разделе](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Щелкните правой кнопкой мыши проект в обозревателе решений и выберите **свойства**.

2. Выберите **выпуска** или **отладки** строится на основе **конфигурации** списка.

2. Выберите **построения** параметры и нажмите кнопку **Дополнительно** кнопки.

    В Visual Basic выберите **компиляции** параметры и **Дополнительные параметры компиляции** вместо кнопки.

3. Выберите **полного**, **переносимой**, или **pdb_only** в **отладочная информация** списка (**создать отладочную информацию** в Visual Basic).

    Описание формата является самой последней форматом кросс платформенных .NET Core. Дополнительные сведения о параметрах см. в разделе [диалоговое окно «Дополнительные параметры построения» (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

    ![Создать файл PDB для сборок в C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. Построить проект.

    Файлы символов создаются в той же папке, что исполняемый файл или основного выходного файла.

### <a name="generate-symbol-files-for-a-c-project"></a>Создавать файлы символов для проекта C++

1. Щелкните правой кнопкой мыши проект в обозревателе решений и выберите **свойства**.

2. Выберите **выпуска** или **отладки** строится на основе **конфигурации** списка.

2. В разделе **компоновщика > Отладка**, выберите требуемого параметры для **создать отладочную информацию**.

    Подробные сведения о параметры проекта для конфигурации отладки в C++ см. в разделе [параметры для конфигурации отладки C++ проекта](../debugger/project-settings-for-a-cpp-debug-configuration.md).

4. Настройка параметров для создания файлов базы данных программы

    В большинстве проектов C++, значение по умолчанию — `$(OutDir)$(TargetName).pdb`, служащего для создания PDB-файлы в выходную папку.

    ![Создать файл PDB для сборок в C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. Построить проект.

    Файлы символов создаются в той же папке, что исполняемый файл или основного выходного файла.
  
## <a name="see-also"></a>См. также  
 [Укажите в отладчике Visua Studio файлов символов (.pdb) и исходных файлов](../debugger/debugger-settings-and-preparation.md)  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md)
