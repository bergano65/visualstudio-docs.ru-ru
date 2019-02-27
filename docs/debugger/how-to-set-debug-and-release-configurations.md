---
title: Настроить отладку и выпуск конфигураций | Документация Майкрософт
ms.date: 10/05/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0bf0da5f15bbb59c2898af0dc0bfec1105cbab0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715431"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Настройка конфигураций отладки и выпуска в Visual Studio

Проекты Visual Studio имеют отдельные конфигурации выпуска и отладки для вашей программы. Производится построение отладочной версии для отладки и версии выпуска для окончательного выпуска.

В конфигурации отладки программы компилируется с полной символической отладочной информацией и без оптимизации. Оптимизация усложняет отладку, поскольку усложняется связь между исходным кодом и сгенерированными инструкциями.

Конфигурация программы для выпуска полностью оптимизируется и его не содержит символической отладочной информации. Для управляемого кода и кода C++, могут создаваться отладочной информации в PDB-файлы, [в зависимости от параметров компилятора](#BKMK_symbols_release) , которые используются. Создание PDB-файлов может оказаться полезным в том случае, если позднее возникнет необходимость в отладке версии выпуска.

Дополнительные сведения о конфигурациях сборки см. в статье [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).

Конфигурацию сборки можно изменить в меню **Сборка** на панели инструментов или на страницах свойств проекта. Страницы свойств проекта зависят от конкретного языка. Следующая процедура показывает, как изменить конфигурацию сборки из меню и на панели инструментов. Дополнительные сведения о том, как изменить конфигурацию построения в проектах на разных языках, см. в разделе [см. также](#see-also) разделе ниже.

## <a name="change-the-build-configuration"></a>Измените конфигурацию сборки

Чтобы изменить конфигурацию сборки, либо:

* Из **построения** меню, выберите **Configuration Manager**, а затем выберите **Отладка** или **выпуска**.

или

* На панели инструментов выберите либо **Отладка**, либо **Выпуск** из списка **Конфигурации решения**.

  ![Конфигурация построения панели инструментов](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Создание файлов символов (.pdb) для сборки (C#, C++, Visual Basic, F#)

Вы можете создать файлы символов (.pdb) и что отладочную информацию для включения. Для большинства типов проектов компилятор создает файлы символов по умолчанию для отладки и сборки выпуска, а другие параметры по умолчанию зависящих от типа проекта и версии Visual Studio.

> [!IMPORTANT]
> Отладчик загружает PDB-файл для исполняемого файла, только если он точно соответствует PDB-файлу, который был создан при сборке исполняемого файла (то есть это должен быть либо оригинальный PDB-файл, либо его копия). Дополнительные сведения см. в статье [Почему Visual Studio требует, чтобы файлы символов отладчика точно соответствовали двоичным файлам, с которыми они были собраны?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Каждый тип проекта может иметь другим способом настройки этих параметров.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Создать файлы символов для C#, ASP.NET или проекта Visual Basic

Подробные сведения о параметрах проекта для конфигураций отладки в C# или Visual Basic, см. в разделе [параметры для проекта C# конфигурации отладки](../debugger/project-settings-for-csharp-debug-configurations.md) или [параметры для отладки Visual Basic проекта конфигурации](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Выберите проект в Обозревателе решений.

2. Выберите **свойства** значок (или нажмите клавишу **Alt + ВВОД**).

3. В боковой панели навигации выберите **построения** (или **компиляции** в Visual Basic).

4. В **конфигурации** выберите **Отладка** или **выпуска**.

5. Выберите **Дополнительно** кнопку (или **Дополнительные параметры компиляции** кнопки в Visual Basic).

6. В **отладочную информацию** списка (или **создать отладочную информацию** списка в Visual Basic), выберите **полный**, **только Pdb**, или **Переносимой**.

   Переносимый формат является самой последней кросс платформенных для .NET Core. Дополнительные сведения о параметрах см. в разделе [диалоговое окно «Дополнительные параметры построения» (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Создать файл PDB для сборок в C# ](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Построить проект.

   Компилятор создает файлы символов в той же папке, как исполняемый файл или основного выходного файла.

### <a name="generate-symbol-files-for-a-c-project"></a>Создать файлы символов для проекта C++

1. Выберите проект в Обозревателе решений.

2. Выберите **свойства** значок (или нажмите клавишу **Alt + ВВОД**).

3. В **конфигурации** выберите **Отладка** или **выпуска**.

4. В боковой панели навигации выберите **компоновщика > Отладка**, затем выберите параметры для **создать отладочную информацию**.

   Подробные сведения о параметрах проекта для конфигураций отладки в C++ см. в разделе [параметры проекта для C++ конфигурации отладки](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Настройка параметров для **создать файлы базы данных программы**.

   В большинстве проектов C++, значение по умолчанию — `$(OutDir)$(TargetName).pdb`, который создает PDB-файлы в выходную папку.

   ![Создать файл PDB для сборок в C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Построить проект.

   Компилятор создает файлы символов в той же папке, как исполняемый файл или основного выходного файла.

## <a name="see-also"></a> См. также

- [Указание файлов символов (.pdb) и исходных файлов в отладчике Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)<br/>
- [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Параметры проекта для конфигурации отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md)
