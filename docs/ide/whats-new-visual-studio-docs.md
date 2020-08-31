---
title: 'Документация по Visual Studio. Новые возможности выпуска в июле 2020 г. '
titleSuffix: ''
description: Обновления документации Visual Studio за июль 2020 г.
ms.date: 08/06/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: f8f5ac8944120d5a48ab0f199d19376423abd2eb
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2020
ms.locfileid: "88714466"
---
# <a name="visual-studio-docs-whats-new-in-the-docs-for-july-2020"></a>Документация по Visual Studio. Обновления в документации за июль 2020 г.

Узнайте, что изменилось в документации по Visual Studio за июль 2020 г. В этой статье перечислены основные изменения, внесенные в документацию в течение этого периода.

## <a name="code-quality"></a>Качество кода

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

## <a name="containers"></a>Контейнеры

**Новые статьи**

- [Настройка функции "Локальный процесс с Kubernetes"](/visualstudio/containers/configure-local-process-with-kubernetes) (конфигурация YAML для локального процесса с Kubernetes).
- [Использование Локального процесса с Kubernetes (предварительная версия)](/visualstudio/containers/local-process-kubernetes) — перенос Dev Spaces.
- [Принцип работы функции "Локальный процесс с Kubernetes"](/visualstudio/containers/overview-local-process-kubernetes)
  - Локальный процесс для Kubernetes. Добавлен раздел по маршрутизации.
  - Перенос Dev Spaces.

## <a name="cross-platform"></a>Кроссплатформенные

**Обновленные статьи**

- [Журнал изменений (инструменты Visual Studio для Unity, Windows)](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity), версия журнала изменений VSTU увеличена до 4.7.1.0
- [Журнал изменений (инструменты Visual Studio для Unity, Mac)](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity-mac), версия журнала изменений VSTUM увеличена до 2.7.1.0

## <a name="get-started"></a>Начало работы

**Новые статьи**

- [Учебник. Расширение простого консольного приложения C#](/visualstudio/get-started/csharp/tutorial-console-part-2), выпущена первая версия руководства по расширению Sidewalk

## <a name="ide"></a>IDE

**Новые статьи**

- [Рекомендации сообщества разработчиков](/visualstudio/ide/developer-community-guidelines), добавлены рекомендации по DevCom
- [Завершение IntelliSense для неимпортируемых типов и методов расширения](/visualstudio/ide/reference/intellisense-completion-unimported-types-extension-methods)

## <a name="install"></a>Установка

**Новые статьи**

- [Обновление Visual Studio с использованием минимального автономного макета](/visualstudio/install/update-minimal-layout), задокументирована возможность минимального макета
- [Руководство по Visual Studio Enterprise](/visualstudio/install/visual-studio-enterprise-guide) — инструкции по использованию Enterprise.

## <a name="javascript"></a>JavaScript

**Новые статьи**

- [Компиляция кода TypeScript (Node.js)](/visualstudio/javascript/compile-typescript-code-npm) — компиляция и сборка для TypeScript.
- [Компиляция кода TypeScript (ASP.NET Core)](/visualstudio/javascript/compile-typescript-code-nuget) — компиляция и сборка для TypeScript.

## <a name="msbuild"></a>MSBuild

**Новые статьи**

- [Общие метаданные элементв MSBuild](/visualstudio/msbuild/common-msbuild-item-metadata), добавлена таблица в MSBuild для необязательных метаданных с элементами Link и LinkBase
- [Фильтры решений в MSBuild](/visualstudio/msbuild/solution-filters) — фильтры решений MSBuild.

## <a name="test"></a>Тест

**Новые статьи**

- [Отладка и анализ модульных тестов с помощью Обозревателя тестов](/visualstudio/test/debug-unit-tests-with-test-explorer) — работа по улучшению производительности в обозревателе тестов.

**Обновленные статьи**

- [Настройка модульных тестов с помощью файла *.runsettings*](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - Внесены сведения о настройке модульных тестов с помощью файла .runsettings
  - Изменено описание параметра blame, добавлен пример.

## <a name="community-contributors"></a>Участники сообщества

Указанные ниже пользователи в течение этого периода внесли свой вклад в улучшение документации по Visual Studio. Спасибо! Сведения о том, как вносить изменения в документацию по Visual Studio, вы найдете в [руководстве для участников](https://docs.microsoft.com/contribute/).

- [briuk](https://github.com/briuk) — Viktor Briukhanov (2);
- [Youssef1313](https://github.com/Youssef1313) — Youssef Victor (2);
- [ArntWork](https://github.com/ArntWork) — Legolas (1);
- [Asugakoisi](https://github.com/Asugakoisi) — アスガコイシ (1);
- [Delizald](https://github.com/Delizald) — David Elizalde (1);
- [farisachugthai](https://github.com/farisachugthai) — Faris A Chugthai (1);
- [mycalingram](https://github.com/mycalingram) — Mycal (1);
- [tuyen-at-work](https://github.com/tuyen-at-work) — Tuyen Pham (1).
