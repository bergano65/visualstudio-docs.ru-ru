---
title: Настройка конфигураций отладки и выпуска | Документация Майкрософт
description: Настройка конфигураций отладки и выпуска в Visual Studio. Производится построение отладочной версии для отладки и версии выпуска для окончательного выпуска программы.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6f96570f517d24492ecdacb4e45450fa7b7ba1cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908402"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Настройка конфигураций отладки и выпуска в Visual Studio

Проекты Visual Studio имеют отдельные конфигурации выпуска и отладки для вашей программы. Производится построение отладочной версии для отладки и версии выпуска для окончательного выпуска программы.

Отладочная конфигурация программы компилируется с полной символической отладочной информацией и без оптимизации. Оптимизация усложняет отладку, поскольку усложняется связь между исходным кодом и сгенерированными инструкциями.

Конфигурация выпуска для программы полностью оптимизируется и не содержит символической отладочной информации. Для управляемого кода и кода C++ отладочная информация может быть создана в виде PDB-файлов в [зависимости от используемых параметров компилятора](#BKMK_symbols_release). Создание PDB-файлов может оказаться полезным, если позднее возникнет необходимость в отладке версии выпуска.

Дополнительные сведения о конфигурациях сборки см. в статье [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).

Конфигурацию сборки можно изменить в меню **Сборка** на панели инструментов или на страницах свойств проекта. Страницы свойств проекта зависят от конкретного языка. Следующая процедура показывает, как изменить конфигурацию сборки из меню и на панели инструментов. Дополнительные сведения об изменении конфигурации сборки в проектах на разных языках см. в разделе [См. также](#see-also) ниже.

## <a name="change-the-build-configuration"></a>Изменение конфигурации сборки

Для изменения конфигурации сборки сделайте следующее.

* В меню **Сборка** щелкните **Диспетчер конфигураций**, а затем выберите **Отладка** или **Выпуск**.

or

* На панели инструментов выберите либо **Отладка**, либо **Выпуск** из списка **Конфигурации решения**.

  ![конфигурация сборки панелей инструментов](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>Создание файлов символов (PDB) для сборки (C#, C++, Visual Basic, F#)

Можно выбрать создание файлов символов (PDB) и отладочные данные, которые необходимо включить. Для большинства типов проектов компилятор создает файлы символов по умолчанию для отладочных и окончательных сборок, в то время как другие параметры по умолчанию отличаются по типу проекта и версии Visual Studio.

> [!IMPORTANT]
> Отладчик загружает PDB-файл для исполняемого файла, только если он точно соответствует PDB-файлу, который был создан при сборке исполняемого файла (то есть это должен быть либо оригинальный PDB-файл, либо его копия). Дополнительные сведения см. в статье [Почему Visual Studio требует, чтобы файлы символов отладчика точно соответствовали двоичным файлам, с которыми они были собраны?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

Каждый тип проекта может иметь свой способ установки этих параметров.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Создание файлов символов для проекта C#, ASP.NET или Visual Basic

Дополнительные сведения о параметрах проекта для конфигурации отладки C# и Visual Basic см. в статьях [Параметры проектов для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md) и [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Выберите проект в Обозревателе решений.

2. Выберите значок **Свойства** (или нажмите клавишу **ALT+ВВОД**).

3. В боковой области выберите **Сборка** (или **Компилировать** в Visual Basic).

4. В списке **Конфигурация** выберите **Отладка** или **Выпуск**.

5. Нажмите кнопку **Дополнительно** (или **Дополнительные параметры компиляции** в Visual Basic).

6. В списке **Сведения об отладке** (или **Создать сведения об отладке** в Visual Basic) выберите **Полные**, **Только для PDB** или **Переносимые**.

   Переносимый формат разработан относительно недавно для кроссплатформенных приложений .NET Core. Дополнительные сведения о параметрах см. в статье [Диалоговое окно "Дополнительные параметры сборки" (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Создание файлов PDB для сборок в C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Построить проект.

   Компилятор создает файлы символов в той же папке, что и исполняемый файл или основной выходной файл.

### <a name="generate-symbol-files-for-a-c-project"></a>Создание файлов символов для проекта C++

1. Выберите проект в Обозревателе решений.

2. Выберите значок **Свойства** (или нажмите клавишу **ALT+ВВОД**).

3. В списке **Конфигурация** выберите **Отладка** или **Выпуск**.

4. В боковой области выберите **Компоновщик > Отладка**, а затем выберите параметры в разделе **Создать сведения об отладке**.

   Дополнительные сведения о параметрах проекта для конфигурации отладки C++ см. в разделе [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Настройте параметры для раздела **Создание файлов базы данных программы**.

   В большинстве проектов C++ значением по умолчанию является `$(OutDir)$(TargetName).pdb`, которое создает PDB-файлы в выходной папке.

   ![Создание файлов PDB для сборок в C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Построить проект.

   Компилятор создает файлы символов в той же папке, что и исполняемый файл или основной выходной файл.

## <a name="see-also"></a><a name="see-also"></a> См. также

- [Указание файлов символов (PDB) и исходных файлов в отладчике Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).<br/>
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)<br/>
- [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Параметры проекта для конфигурации отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md)