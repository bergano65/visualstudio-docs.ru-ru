---
title: "Компиляция и сборка в Visual Studio для Mac | Документы Майкрософт"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 9005cf64f4b72f39923d6525e78de745d79c3953
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Компиляция и сборка в Visual Studio для Mac

Visual Studio для Mac можно использовать для сборки приложений и создания сборок во время разработки проекта. Важно выполнять раннюю и частую компиляцию и сборку кода, чтобы выявить несоответствия типов и другие ошибки времени компиляции.

## <a name="choosing-a-build-method"></a>Выбор метода сборки:

### <a name="using-the-ide"></a>Использование интегрированной среды разработки

Использование Visual Studio для Mac позволяет мгновенно создавать и запускать сборки, а также сохранять контроль над функциями сборки. Visual Studio для Mac использует в качестве базовой системы сборки MSBuild.

Все проекты и решения, созданные в этой интегрированной среде разработки, будут иметь конфигурацию сборки по умолчанию, определяющую контекст для сборок. Вы можете изменять эти конфигурации или создавать собственные. Создание и изменение конфигураций приводит к автоматическому обновлению файла проекта, который затем используется в MSBuild для сборки проекта.  

Дополнительные сведения о сборке проектов и решений в интегрированной среде разработки см. в разделе [Сборка и очистка проектов и решений](~/building-and-cleaning-projects-and-solutions.md).

Visual Studio для Mac также можно использовать для выполнения следующих задач:

* Изменение выходного пути. Он настраивается в параметрах проекта:

    ![Изменение выходного пути](media/compiling-and-building-image4.png)

* Изменение уровня детализации для результатов сборки:

    ![Изменение детализации сборки](media/compiling-and-building-image5.png)

* Добавление настраиваемых команд до, во время или после сборки или очистки:

    ![Добавление настраиваемых команд](media/compiling-and-building-image6.png)

### <a name="building-from-command-line"></a>Сборка из командной строки

Подсистему сборки MSBuild можно использовать для сборки приложений с помощью командной строки.

Дополнительные сведения об использовании MSBuild см. в разделе [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

### <a name="using-visual-studio-team-services"></a>Использование Visual Studio Team Services

* [Сборка приложения Xamarin](https://www.visualstudio.com/docs/build/apps/mobile/xamarin)
* [Непрерывная интеграция с помощью Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)