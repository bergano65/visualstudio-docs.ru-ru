---
title: Общие свойства проекта (Android C++) | Документы Майкрософт
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 4bb6f26fe40b639b43cb803577a785fa9b48823d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949913"
---
# <a name="general-project-properties-android-c"></a>Общие свойства проекта (Android C++)

Свойство. | Описание | Варианты
--- | ---| ---
Выходной каталог | Указывает относительный путь к выходному каталогу файлов; может включать в себя переменные среды.
Промежуточный каталог | Указывает относительный путь к промежуточному каталогу файлов; может включать в себя переменные среды.
Целевое имя | Задает имя файла, создаваемого проектом.
Конечное расширение | Указывает расширение файла, которое будет создано этим проектом. (Пример: *EXE* или *DLL*.)
Расширения для удаления при очистке | Спецификация из подстановочных знаков (разделитель — точка с запятой), определяющая, какие файлы в промежуточном каталоге нужно удалять при очистке или перестроении.
Файл журнала сборки | Определяет файл журнала сборки, в который будет вестись запись, если ведение журнала включено.
Набор инструментов платформы | Задает набор инструментов, используемый для сборки текущей конфигурации; если не указан, используется набор инструментов по умолчанию
Тип конфигурации | Определяет тип выходных данных, создаваемых этой конфигурацией. | **Динамическая библиотека (.so)**  — динамическая библиотека (*.so*)<br>**Статическая библиотека (.a)** — статическая библиотека (*.a*)<br>**Служебная программа** — служебная программа<br>**Makefile** — файл Makefile<br>
Целевой уровень API | Целевой уровень API NDK Android для этой конфигурации.
Использование STL | Указывает, какую стандартную библиотеку C++ следует использовать для этой конфигурации. | **Минимальная библиотека среды выполнения C++ (система)**<br>**Статическая библиотека среды выполнения C++ (gabi++_static)**<br>**Общая библиотека среды выполнения C++ (gabi++_shared)**<br>**Статическая библиотека среды выполнения STLport (stlport_static)**<br>**Общая библиотека среды выполнения STLport (stlport_shared)**<br>**Статическая библиотека GNU STL (gnustl_static)**<br>**Общая библиотека GNU STL (gnustl_shared)**<br>**Статическая библиотека LLVM libc++ (c++_static)**<br>**Общая библиотека LLVM libc++ (c++_shared)**<br>
Режим Thumb | Создайте код, выполняемый для микроархитектуры Thumb. Применимо только к архитектуре ARM. | **Thumb**<br>**ARM**<br>**Отключено**<br>
