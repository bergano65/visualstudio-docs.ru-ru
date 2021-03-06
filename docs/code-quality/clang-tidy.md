---
title: Использование Clang в Visual Studio
ms.date: 10/04/2019
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.clangtidy
author: frozenpandaman
ms.author: efessler
ms.workload:
- cplusplus
ms.openlocfilehash: 25320da07249abee0ab0cddd48662585a7a809dd
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846751"
---
# <a name="using-clang-tidy-in-visual-studio"></a>Использование Clang в Visual Studio

Анализ кода изначально поддерживает Clang для проектов MSBuild и CMak независимо [от](https://clang.llvm.org/extra/clang-tidy/) того, используются ли наборы инструментов CLANG или компилятором MSVC. Clangные проверки могут выполняться как часть анализа фонового кода, отображаться в виде предупреждений в редакторе (волнистых линий) и отображаться в Список ошибок.

Чтобы использовать Clang, компонент "C++ средства Clang для Windows" должен быть установлен с помощью Visual Studio Installer.

Clang — это средство анализа по умолчанию при использовании набора инструментов LLVM/Clang-CL, доступных как в MSBuild, так и в CMak. Его можно настроить для запуска параллельно или вместо стандартного анализа кода при использовании набора инструментов КОМПИЛЯТОРОМ MSVC. При использовании набора инструментов Clang-CL анализ кода Майкрософт будет недоступен.

Clang выполняется после успешной компиляции; чтобы получить результаты Clang, может потребоваться устранить ошибки исходного кода.


## <a name="msbuild"></a>MSBuild

Вы можете настроить Clang для запуска как часть анализа кода и выполнять сборку на странице " **анализ кода** > **общие** " в окно свойств проекта. Параметры для настройки средства можно найти в подменю Clang.

Дополнительные сведения см. [в разделе инструкции. Установка свойств анализа кода для C/C++ Projects](../code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="cmake"></a>CMake

В проектах CMak можно настроить Clang проверки в пределах `CMakeSettings.json`. После открытия щелкните "изменить JSON" в правом верхнем углу редактора параметров проекта CMak. Распознаются следующие ключи:

- `enableMicrosoftCodeAnalysis`: включает анализ кода Майкрософт
- `enableClangTidyCodeAnalysis`: включает анализ Clangности
- `clangTidyChecks`: конфигурация с Clang, указанная в виде списка с разделителями-запятыми, т. е. проверки на включение или отключение.

Если не указано ни одного из параметров "включить", Visual Studio выберет средство анализа, соответствующее используемому набору инструментов платформы.

## <a name="warning-display"></a>Отображение предупреждений

Clangные запуски приводят к отображению предупреждений в Список ошибок и в виде волнистых линий в соответствующих разделах кода. Используйте столбец Category (категория) в Список ошибок для сортировки и упорядочения предупреждений Clang. Можно настроить предупреждения в редакторе, установив параметр "отключить неподчеркнутые коды анализа кода" в меню " **сервис** > **Параметры**".

## <a name="clang-tidy-configuration"></a>Конфигурация с Clang

Можно настроить проверки, выполняемые Clang в Visual Studio с помощью параметра **Clang-configure checks** . Эти входные данные предоставляются в аргументе **--checks** средства. Любую дальнейшую настройку можно добавить в пользовательские файлы **. Clang** . Дополнительные сведения см. в [документации по Clang на LLVM.org](https://clang.llvm.org/extra/clang-tidy/) .

## <a name="see-also"></a>См. также:

- [Поддержка Clang/LLVM для проектов MSBuild](https://devblogs.microsoft.com/cppblog/clang-llvm-support-for-msbuild-projects/)
- [Поддержка Clang/LLVM для проектов CMak](https://devblogs.microsoft.com/cppblog/visual-studio-cmake-support-clang-llvm-cmake-3-14-vcpkg-and-performance-improvements/)
