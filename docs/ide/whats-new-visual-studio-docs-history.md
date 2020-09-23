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
ms.openlocfilehash: 8505f98163c57fe276bcf4c76195fe843300394f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809470"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>История новых возможностей в документации по Visual Studio

Добро пожаловать в историю изменений документации по Visual Studio. В этом разделе приведены основные изменения в документации до августа 2020 г. (начиная с июля 2020 г.). Последние изменения см. в разделе [Документация по Visual Studio. Обновления в документации за июль 2020 г.](whats-new-visual-studio-docs.md)

## <a name="july-2020"></a>Июль 2020 г.
### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1417. Не используйте в строковых параметрах `OutAttribute` для P/Invoke](../code-quality/ca1417.md). Добавлена документация по CA1417.
- [CA1805. Не делайте лишних инициализаций.](../code-quality/ca1805.md) Добавлена документация по CA1805.
- [CA1836. Отдавайте предпочтение IsEmpty перед Count (при наличии)](../code-quality/ca1836.md). Добавлена документация по CA1836 (предпочтение IsEmpty вместо Count)
- [CA2016. Переадресуйте параметр CancellationToken методам, которые его принимают](../code-quality/ca2016.md). Документ CA2016 (переадресация параметра CancellationToken методам, которые его принимают).
- [CA2350. Убедитесь, что входные данные DataTable.ReadXml() являются доверенными](../code-quality/ca2350.md) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2351. Убедитесь, что входные данные DataSet.ReadXml() являются доверенными](../code-quality/ca2351.md) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2352. Ненадежные данные DataSet или DataTable в сериализуемом типе могут быть уязвимыми для атак удаленного выполнения кода](../code-quality/ca2352.md) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2353. Ненадежные данные DataSet или DataTable в сериализуемом типе](../code-quality/ca2353.md) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2354. Ненадежные данные DataSet или DataTable в графе десериализованных объектов могут быть уязвимыми для атаки удаленного выполнения кода](../code-quality/ca2354.md) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2355. Ненадежные данные DataSet или DataTable в графе десериализованных объектов](../code-quality/ca2355.md) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2356. Ненадежные данные DataSet или DataTable в графе десериализованных веб-объектов](../code-quality/ca2356.md) (базовая документация по правилам десериализации DataSet и DataTable).

### <a name="containers"></a>Контейнеры

**Новые статьи**

- [Настройка функции "Локальный процесс с Kubernetes"](../containers/configure-local-process-with-kubernetes.md) (конфигурация YAML для локального процесса с Kubernetes).
- [Использование Локального процесса с Kubernetes (предварительная версия)](../containers/local-process-kubernetes.md) — перенос Dev Spaces.
- [Принцип работы функции "Локальный процесс с Kubernetes"](../containers/overview-local-process-kubernetes.md)
  - Локальный процесс для Kubernetes. Добавлен раздел по маршрутизации.
  - Перенос Dev Spaces.

### <a name="cross-platform"></a>Кроссплатформенные

**Обновленные статьи**

- [Журнал изменений (инструменты Visual Studio для Unity, Windows)](../cross-platform/change-log-visual-studio-tools-for-unity.md), версия журнала изменений VSTU увеличена до 4.7.1.0
- [Журнал изменений (инструменты Visual Studio для Unity, Mac)](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md), версия журнала изменений VSTUM увеличена до 2.7.1.0

### <a name="get-started"></a>Начало работы

**Новые статьи**

- [Учебник. Расширение простого консольного приложения C#](../get-started/csharp/tutorial-console-part-2.md), выпущена первая версия руководства по расширению Sidewalk

### <a name="ide"></a>IDE

**Новые статьи**

- [Рекомендации сообщества разработчиков](./developer-community-guidelines.md), добавлены рекомендации по DevCom
- [Завершение IntelliSense для неимпортируемых типов и методов расширения](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Установка

**Новые статьи**

- [Обновление Visual Studio с использованием минимального автономного макета](../install/update-minimal-layout.md), задокументирована возможность минимального макета
- [Руководство по Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) — инструкции по использованию Enterprise.

### <a name="javascript"></a>JavaScript

**Новые статьи**

- [Компиляция кода TypeScript (Node.js)](../javascript/compile-typescript-code-npm.md) — компиляция и сборка для TypeScript.
- [Компиляция кода TypeScript (ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) — компиляция и сборка для TypeScript.

### <a name="msbuild"></a>MSBuild

**Новые статьи**

- [Общие метаданные элементв MSBuild](../msbuild/common-msbuild-item-metadata.md), добавлена таблица в MSBuild для необязательных метаданных с элементами Link и LinkBase
- [Фильтры решений в MSBuild](../msbuild/solution-filters.md) — фильтры решений MSBuild.

### <a name="test"></a>Тест

**Новые статьи**

- [Отладка и анализ модульных тестов с помощью Обозревателя тестов](../test/debug-unit-tests-with-test-explorer.md) — работа по улучшению производительности в обозревателе тестов.

**Обновленные статьи**

- [Настройка модульных тестов с помощью файла *.runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Внесены сведения о настройке модульных тестов с помощью файла .runsettings
  - Изменено описание параметра blame, добавлен пример.