---
title: Компилирование и сборка
description: В этой статье описывается компиляция и сборка проектов и решений в Visual Studio для Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.topic: overview
ms.openlocfilehash: d5613a47785f1bb3fbb2a56f8458bba1946930e7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719805"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Компиляция и сборка в Visual Studio для Mac

Visual Studio для Mac можно использовать для сборки приложений и создания сборок во время разработки проекта. Важно выполнять раннюю и частую компиляцию и сборку кода, чтобы выявить несоответствия типов и другие ошибки времени компиляции.

## <a name="building-from-the-ide"></a>Создание в интегрированной среде разработки

Использование Visual Studio для Mac позволяет мгновенно создавать и запускать сборки, а также сохранять контроль над функциями сборки. Visual Studio для Mac использует в качестве базовой системы сборки MSBuild.

Все проекты и решения, созданные в этой интегрированной среде разработки, будут иметь конфигурацию сборки по умолчанию, определяющую контекст для сборок. Вы можете изменять эти конфигурации или создавать собственные. Создание и изменение конфигураций приводит к автоматическому обновлению файла проекта, который затем используется в MSBuild для сборки проекта.

Дополнительные сведения о сборке проектов и решений в интегрированной среде разработки см. в разделе [Сборка и очистка проектов и решений](building-and-cleaning-projects-and-solutions.md).

Visual Studio для Mac также можно использовать для выполнения следующих задач:

* Изменение выходного пути. Он настраивается в параметрах проекта:

    ![Изменение выходного пути](media/compiling-and-building-image4.png)

* Изменение уровня детализации для результатов сборки:

    ![Изменение детализации сборки](media/compiling-and-building-image5.png)

* Добавление настраиваемых команд до, во время или после сборки или очистки:

    ![Добавление настраиваемых команд](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Сборка из командной строки

Подсистему сборки MSBuild можно использовать для сборки приложений с помощью командной строки.

Дополнительные сведения об использовании MSBuild см. в разделе [MSBuild](/visualstudio/msbuild/msbuild).

## <a name="building-from-azure-pipelines"></a>Построение из Azure Pipelines

* [Сборка приложения Xamarin](/vsts/pipelines/apps/mobile/xamarin?view=vsts&preserve-view=true&tabs=vsts)
* [Непрерывная интеграция с помощью Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>См. также раздел

- [Компиляция и сборка (Visual Studio в Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)