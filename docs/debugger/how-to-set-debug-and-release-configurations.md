---
title: Настройка конфигураций отладки и выпуска | Документация Майкрософт
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
ms.openlocfilehash: 75acf0a3a821b4d2561ea14e583e71761b8b476e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925481"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Настройка конфигураций отладки и выпуска в Visual Studio

Проекты Visual Studio имеют отдельные конфигурации выпуска и отладки для вашей программы. Вы создаете отладочную версию для отладки и версию выпуска для окончательного распространения выпуска.

В конфигурации отладки программа компилируется с полной символьной отладочной информацией и без оптимизации. Оптимизация усложняет отладку, поскольку усложняется связь между исходным кодом и сгенерированными инструкциями.

Конфигурация выпуска программы не имеет символьной отладочной информации и полностью оптимизирована. Для управляемого кода C++ и кода отладочная информация может быть создана в PDB-файлах в [зависимости от используемых параметров компилятора](#BKMK_symbols_release) . Создание PDB-файлов может оказаться полезным, если в дальнейшем потребуется Отладка окончательной версии.

Дополнительные сведения о конфигурациях сборки см. в статье [Общие сведения о конфигурациях сборки](../ide/understanding-build-configurations.md).

Конфигурацию сборки можно изменить в меню **Сборка** на панели инструментов или на страницах свойств проекта. Страницы свойств проекта зависят от конкретного языка. Следующая процедура показывает, как изменить конфигурацию сборки из меню и на панели инструментов. Дополнительные сведения о том, как изменить конфигурацию сборки в проектах на разных языках, см. в разделе [см. также](#see-also) ниже.

## <a name="change-the-build-configuration"></a>Изменение конфигурации сборки

Чтобы изменить конфигурацию сборки, выполните одно из следующих действий.

* В меню **Сборка** выберите **Configuration Manager**, а затем выберите **Отладка** или **выпуск**.

или диспетчер конфигурации служб

* На панели инструментов выберите либо **Отладка**, либо **Выпуск** из списка **Конфигурации решения**.

  ![Конфигурация сборки панелей инструментов](../debugger/media/toolbarbuildconfiguration.png "Тулбарбуилдконфигуратион")

## <a name="BKMK_symbols_release"></a>Создание файлов символов (. pdb) для сборки (C#, C++, Visual Basic,) F#

Можно выбрать создание файлов символов (. pdb) и включаемых отладочных данных. Для большинства типов проектов компилятор создает файлы символов по умолчанию для отладочных и окончательных сборок, в то время как другие параметры по умолчанию отличаются по типу проекта и версии Visual Studio.

> [!IMPORTANT]
> Отладчик загружает PDB-файл для исполняемого файла, только если он точно соответствует PDB-файлу, который был создан при сборке исполняемого файла (то есть это должен быть либо оригинальный PDB-файл, либо его копия). Дополнительные сведения см. в статье [почему Visual Studio требует, чтобы файлы символов отладчика точно совпадали с двоичными файлами, с которыми они были созданы?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

Каждый тип проекта может иметь другой способ установки этих параметров.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Создание файлов символов для проекта C#, ASP.NET или Visual Basic

Подробные сведения о параметрах проекта для конфигураций отладки C# в или Visual Basic см. в разделе [Параметры C# проекта для конфигурации отладки](../debugger/project-settings-for-csharp-debug-configurations.md) или [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Выберите проект в Обозревателе решений.

2. Выберите значок **Свойства** (или нажмите клавиши **ALT + ВВОД**).

3. В боковой области выберите **Сборка** (или **Скомпилируйте** в Visual Basic).

4. В списке **Конфигурация** выберите Отладка или **выпуск**.

5. Нажмите кнопку **Дополнительно** (или кнопку **Дополнительные параметры компиляции** в Visual Basic).

6. В списке **отладочной информации** (или в списке **создать отладочную информацию** в Visual Basic) выберите **полная**, **только PDB**или Переносимая.

   Переносимый формат — это самый последний кросс-платформенный формат для .NET Core. Дополнительные сведения о параметрах см. в разделе [диалоговое окно "C#дополнительные параметры сборки" ()](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Создать PDB для сборок в C# ](../debugger/media/dbg_project_properties_pdb_csharp.png "Женератепдбсфоркшарп")

7. Построить проект.

   Компилятор создает файлы символов в той же папке, что и исполняемый файл, или основной выходного файла.

### <a name="generate-symbol-files-for-a-c-project"></a>Создание файлов символов для C++ проекта

1. Выберите проект в Обозревателе решений.

2. Выберите значок **Свойства** (или нажмите клавиши **ALT + ВВОД**).

3. В списке **Конфигурация** выберите Отладка или **выпуск**.

4. В боковой области выберите **компоновщик > Отладка**, а затем выберите параметры для **создания отладочной информации**.

   Подробные сведения о параметрах проекта для конфигураций отладки C++в см. в разделе [Параметры C++ проекта для конфигурации отладки](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Настройка параметров для **создания файлов базы данных программы**.

   В большинстве C++ проектов значением по умолчанию является `$(OutDir)$(TargetName).pdb`, которое создает PDB-файлы в выходной папке.

   ![Создать PDB для сборок в C++ ](../debugger/media/dbg_project_properties_pdb_cplusplus.png "Женератепдбсфоркплусплус")

6. Построить проект.

   Компилятор создает файлы символов в той же папке, что и исполняемый файл, или основной выходного файла.

## <a name="see-also"></a> См. также

- [Указание файлов символов (. pdb) и исходных файлов в отладчике Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)<br/>
- [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Параметры проекта для конфигурации отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Практическое руководство. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md)
