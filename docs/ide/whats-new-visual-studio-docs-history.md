---
title: 'Документация по Visual Studio. История изменений '
titleSuffix: ''
description: История новых возможностей в документации по Visual Studio
ms.date: 09/01/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 9f5fc25f6bb25c9471b1de1d464fa6afc4c80b3b
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "89410745"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>История новых возможностей в документации по Visual Studio

Добро пожаловать в историю изменений документации по Visual Studio. В этом разделе приведены основные изменения в документации до августа 2020 г. (начиная с июля 2020 г.). Последние изменения см. в разделе [Документация по Visual Studio. Обновления в документации за июль 2020 г.](whats-new-visual-studio-docs.md)

## <a name="july-2020"></a>Июль 2020 г.
### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1417. Не используйте в строковых параметрах `OutAttribute` для P/Invoke](/visualstudio/code-quality/ca1417). Добавлена документация по CA1417.
- [CA1805. Не делайте лишних инициализаций.](/visualstudio/code-quality/ca1805) Добавлена документация по CA1805.
- [CA1836. Отдавайте предпочтение IsEmpty перед Count (при наличии)](/visualstudio/code-quality/ca1836). Добавлена документация по CA1836 (предпочтение IsEmpty вместо Count)
- [CA2016. Переадресуйте параметр CancellationToken методам, которые его принимают](/visualstudio/code-quality/ca2016). Документ CA2016 (переадресация параметра CancellationToken методам, которые его принимают).
- [CA2350. Убедитесь, что входные данные DataTable.ReadXml() являются доверенными](/visualstudio/code-quality/ca2350) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2351. Убедитесь, что входные данные DataSet.ReadXml() являются доверенными](/visualstudio/code-quality/ca2351) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2352. Ненадежные данные DataSet или DataTable в сериализуемом типе могут быть уязвимыми для атак удаленного выполнения кода](/visualstudio/code-quality/ca2352) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2353. Ненадежные данные DataSet или DataTable в сериализуемом типе](/visualstudio/code-quality/ca2353) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2354. Ненадежные данные DataSet или DataTable в графе десериализованных объектов могут быть уязвимыми для атаки удаленного выполнения кода](/visualstudio/code-quality/ca2354) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2355. Ненадежные данные DataSet или DataTable в графе десериализованных объектов](/visualstudio/code-quality/ca2355) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2356. Ненадежные данные DataSet или DataTable в графе десериализованных веб-объектов](/visualstudio/code-quality/ca2356) (базовая документация по правилам десериализации DataSet и DataTable).

### <a name="containers"></a>Контейнеры

**Новые статьи**

- [Настройка функции "Локальный процесс с Kubernetes"](/visualstudio/containers/configure-local-process-with-kubernetes) (конфигурация YAML для локального процесса с Kubernetes).
- [Использование Локального процесса с Kubernetes (предварительная версия)](/visualstudio/containers/local-process-kubernetes) — перенос Dev Spaces.
- [Принцип работы функции "Локальный процесс с Kubernetes"](/visualstudio/containers/overview-local-process-kubernetes)
  - Локальный процесс для Kubernetes. Добавлен раздел по маршрутизации.
  - Перенос Dev Spaces.

### <a name="cross-platform"></a>Кроссплатформенные

**Обновленные статьи**

- [Журнал изменений (инструменты Visual Studio для Unity, Windows)](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity), версия журнала изменений VSTU увеличена до 4.7.1.0
- [Журнал изменений (инструменты Visual Studio для Unity, Mac)](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity-mac), версия журнала изменений VSTUM увеличена до 2.7.1.0

### <a name="get-started"></a>Начало работы

**Новые статьи**

- [Учебник. Расширение простого консольного приложения C#](/visualstudio/get-started/csharp/tutorial-console-part-2), выпущена первая версия руководства по расширению Sidewalk

### <a name="ide"></a>IDE

**Новые статьи**

- [Рекомендации сообщества разработчиков](/visualstudio/ide/developer-community-guidelines), добавлены рекомендации по DevCom
- [Завершение IntelliSense для неимпортируемых типов и методов расширения](/visualstudio/ide/reference/intellisense-completion-unimported-types-extension-methods)

### <a name="install"></a>Установка

**Новые статьи**

- [Обновление Visual Studio с использованием минимального автономного макета](/visualstudio/install/update-minimal-layout), задокументирована возможность минимального макета
- [Руководство по Visual Studio Enterprise](/visualstudio/install/visual-studio-enterprise-guide) — инструкции по использованию Enterprise.

### <a name="javascript"></a>JavaScript

**Новые статьи**

- [Компиляция кода TypeScript (Node.js)](/visualstudio/javascript/compile-typescript-code-npm) — компиляция и сборка для TypeScript.
- [Компиляция кода TypeScript (ASP.NET Core)](/visualstudio/javascript/compile-typescript-code-nuget) — компиляция и сборка для TypeScript.

### <a name="msbuild"></a>MSBuild

**Новые статьи**

- [Общие метаданные элементв MSBuild](/visualstudio/msbuild/common-msbuild-item-metadata), добавлена таблица в MSBuild для необязательных метаданных с элементами Link и LinkBase
- [Фильтры решений в MSBuild](/visualstudio/msbuild/solution-filters) — фильтры решений MSBuild.

### <a name="test"></a>Тест

**Новые статьи**

- [Отладка и анализ модульных тестов с помощью Обозревателя тестов](/visualstudio/test/debug-unit-tests-with-test-explorer) — работа по улучшению производительности в обозревателе тестов.

**Обновленные статьи**

- [Настройка модульных тестов с помощью файла *.runsettings*](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - Внесены сведения о настройке модульных тестов с помощью файла .runsettings
  - Изменено описание параметра blame, добавлен пример.