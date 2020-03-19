---
title: Компилирование и сборка
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b5f00b3e71f0deb15d6266640db39751f2ae22f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "76269104"
---
# <a name="compile-and-build-in-visual-studio"></a>Компиляция и сборка в Visual Studio

Начальные сведения о сборке в IDE см. в разделе [Пошаговое руководство. Построение приложения](walkthrough-building-an-application.md).

Сборку приложения можно выполнять с помощью интегрированной среды разработки Visual Studio, программ командной строки MSBuild и Azure Pipelines:

| Метод построения | Преимущества |
| --- |--- | --- |
| IDE |— Немедленное создание сборок и тестирование их в отладчике.<br />— Запуск многопроцессорных сборок для проектов C++ и C#.<br />— Настройка различных аспектов системы сборки. |
| CMake | – Сборка проектов с помощью средства CMake.<br />– Использование одной и той же системы сборки на платформах Linux и Windows. |
| Командная строка MSBuild| — Сборка проектов без установки Visual Studio.<br />— Запуск многопроцессорных сборок для всех типов проектов.<br />— Настройка большинства аспектов системы сборки.|
| Azure Pipelines | — Автоматизация процесса сборки в рамках конвейера непрерывной интеграции или поставки.<br />— Применение автоматических тестов для каждой сборки.<br />— Использование практически неограниченных облачных ресурсов для процессов сборки.<br />— Возможность изменения рабочего процесса сборки и создания процедур сборки с подробно настраиваемыми задачами.|

В этом разделе подробно рассматривается сборка на основе IDE. Дополнительные сведения о других методах см. в разделах [MSBuild](../msbuild/msbuild.md) и [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) соответственно.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Компиляция и сборка в Visual Studio для Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Общие сведения о сборке из IDE

При создании проекта среда Visual Studio создает для него конфигурации сборки по умолчанию, а также содержащее проект решение.  Эти конфигурации определяют, как выполняется сборка и развертывание решений и проектов. В частности, используются уникальные конфигурации проектов для разных целевых платформ (например, Windows или Linux) и типов сборки (например, отладка или выпуск). Вы можете как угодно изменять эти конфигурации и при необходимости создавать свои собственные.

Начальные сведения о сборке в IDE см. в разделе [Пошаговое руководство. Построение приложения](walkthrough-building-an-application.md).

Затем ознакомьтесь с разделом [Построение и очистка проектов и решений в Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md), чтобы узнать о настройке разных аспектов процесса. Настройки включают [изменение выходных каталогов](how-to-change-the-build-output-directory.md), [указание настраиваемых событий построения](specifying-custom-build-events-in-visual-studio.md), [управление зависимостями проекта](how-to-create-and-remove-project-dependencies.md), [управление файлами журнала построения](how-to-view-save-and-configure-build-log-files.md) и [отключение предупреждений компилятора](how-to-suppress-compiler-warnings.md).

После этого вы можете познакомиться с другими задачами:
- [Общие сведения о конфигурациях построения](understanding-build-configurations.md)
- [Общие сведения о платформах построения](understanding-build-platforms.md)
- [Управление свойствами проектов и решений](managing-project-and-solution-properties.md)
- Назначение событий построения в [C#](how-to-specify-build-events-csharp.md) и [Visual Basic](how-to-specify-build-events-visual-basic.md)
- [Задание параметров сборок](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="see-also"></a>См. также раздел

- [Сборка (компиляция) проектов веб-узлов](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [Компиляция и сборка (Visual Studio для Mac)](/visualstudio/mac/compiling-and-building)
- [Проекты CMake в Visual Studio](/cpp/build/cmake-projects-in-visual-studio)
