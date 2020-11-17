---
title: 'Документация по Visual Studio. История изменений '
titleSuffix: ''
description: История новых возможностей в документации по Visual Studio
ms.date: 10/04/2020
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
ms.openlocfilehash: 2314965dad6c77e749a62946f3372993813240bb
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414507"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>История новых возможностей в документации по Visual Studio

Добро пожаловать в историю изменений документации по Visual Studio. В этой статье приведены основные изменения в документации до октября 2020 г. (начиная с июля 2020 г.). Последние изменения см. в разделе [Документация по Visual Studio. Обновления в документации за июль 2020 г.](whats-new-visual-studio-docs.md)

## <a name="september-2020"></a>Сентябрь 2020 г.
### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1416. Проверка совместимости платформы](/dotnet/fundamentals/code-analysis/quality-rules/ca1416) — задокументировано исправление CA1416 "Проверка совместимости платформы"
- [CA1834. Использование StringBuilder.Append(char) для строк с одним символом](/dotnet/fundamentals/code-analysis/quality-rules/ca1834) — документация по CA1834

**Обновленные возможности**

- [Обзор анализа исходного кода](../code-quality/roslyn-analyzers-overview.md) — обновления анализа кода для рефакторинга .NET
- [Настройка анализа качества кода](../code-quality/use-roslyn-analyzers.md) — обновления анализа кода для рефакторинга .NET

### <a name="containers"></a>Контейнеры

**Новые статьи**

- [Локальный процесс с Kubernetes](../containers/bridge-to-kubernetes.md) — переименование функции "Локальный процесс с Kubernetes" в Bridge to Kubernetes
- [Как работает Bridge to Kubernetes](../containers/overview-bridge-to-kubernetes.md) — переименование функции "Локальный процесс с Kubernetes" в Bridge to Kubernetes

### <a name="deployment"></a>Развертывание

**Обновленные статьи**

- [Развертывание приложения в папке, IIS, Azure или другом расположении](../deployment/deploying-applications-services-and-components-resources.md) — обновления развертывания.
- [Развертывание приложения в папку с помощью Visual Studio](../deployment/quickstart-deploy-to-local-folder.md) — обновления, касающиеся развертывания

### <a name="ide"></a>IDE

**Новые статьи**

- [Новый интерфейс GIT в Visual Studio (предварительная версия)](./git-with-visual-studio.md) — добавлено содержимое о новом интерфейсе GIT (предварительная версия)
- [Соглашения о форматировании EditorConfig на C++](./cpp-editorconfig-properties.md) — новая статья
- [Что такое GitHub Codespaces? (предварительная версия)](./codespaces/codespaces-overview.md) — добавлено содержимое о Codespaces (предварительная версия)
- [Настройка codespace (предварительная версия)](./codespaces/customize-codespaces.md) — добавлено содержимое о Codespaces (предварительная версия)
- [Поддерживаемые функции Visual Studio (предварительная версия)](./codespaces/supported-features-codespaces.md) — добавлено содержимое о Codespaces (предварительная версия)
- [Использование Visual Studio с codespace (предварительная версия)](./codespaces/use-visual-studio-with-codespaces.md) — добавлено содержимое о Codespaces (предварительная версия)

**Обновленные статьи**

- [Параметры соглашений о написании кода .NET в EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) — обновление editorconfig
- [Языковые соглашения](/dotnet/fundamentals/code-analysis/style-rules/language-rules) — отсутствовали примеры

### <a name="install"></a>Установка

**Новые статьи**

- [Visual Studio на устройствах ARM](../install/visual-studio-on-arm-devices.md) — добавлен документ о Visual Studio на ARM

**Обновленные статьи**

- [Исправление ошибок сети при установке или использовании Visual Studio](../install/troubleshooting-network-related-errors-in-visual-studio.md) — добавлено описание решения проблемы с аварийным завершением работы прокси-сервера при авторизации

### <a name="profiling"></a>Профилирование

**Обновленные статьи**

- [Измерение использования памяти в Visual Studio](../profiling/memory-usage.md) — обновления в обзоре возможностей профилирования
- [PerfTips](../profiling/perftips.md) — обновления в обзоре возможностей профилирования
- [Первое знакомство со средствами профилирования](../profiling/profiling-feature-tour.md) — обновления в обзоре возможностей профилирования
- [Запуск средств профилирования с отладчиком или без него](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
  - Обновления в обзоре возможностей профилирования
  - Улучшения производительности

## <a name="august-2020"></a>Август 2020 г.
### <a name="azure"></a>Azure

**Новые статьи**

- [Добавление Azure Application Insights с использованием Подключенных служб Visual Studio](../azure/azure-app-insights-add-connected-service.md) — Подключенные службы для VS 2019 16.7
- [Добавление Кэша Azure для Redis с использованием Подключенных служб Visual Studio](../azure/azure-cache-for-redis-add-connected-service.md) — Подключенные службы для VS 2019 16.7
- [Добавление Azure Cosmos DB в приложение с использованием Подключенных служб Visual Studio](../azure/azure-cosmosdb-add-connected-service.md) — Подключенные службы для VS 2019 16.7
- [Добавление Azure SignalR с использованием Подключенных служб Visual Studio](../azure/azure-signalr-add-connected-service.md) — Подключенные службы для VS 2019 16.7
- [Добавление подключения к Базе данных SQL Azure](../azure/azure-sql-database-add-connected-service.md) — Подключенные службы для VS 2019 16.7

**Обновленные статьи**

- [Добавление хранилища Azure с использованием подключенных служб Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Подключенные службы для VS 2019 16.7.
  - Статья о подключенных службах службы хранилища Azure: обновление пользовательского интерфейса обновления и поддерживаемых типов проектов.

### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1310. Определите StringComparison для правильности](/dotnet/fundamentals/code-analysis/quality-rules/ca1310) — добавлена документация по CA1310 и обновлена документация по CA1307.
- [CA1837. Используйте Environment.ProcessId вместо Process.GetCurrentProcess().Id](/dotnet/fundamentals/code-analysis/quality-rules/ca1837) — документация по CA1837.
- [CA1838. Не используйте строковые параметры `StringBuilder` для P/Invoke](/dotnet/fundamentals/code-analysis/quality-rules/ca1838) — добавлена документация по CA1838.
- [CA2008. Не создавайте задачи без передачи TaskScheduler](/dotnet/fundamentals/code-analysis/quality-rules/ca2008) — добавлена документация по CA2008.
- [CA2249. Попробуйте использовать String.Contains вместо String.IndexOf](/dotnet/fundamentals/code-analysis/quality-rules/ca2249) — добавлена документация по СА2249.
- [CA2361. Убедитесь, что автоматически сформированный класс, который содержит DataSet.ReadXml(), не используется с ненадежными данными](/dotnet/fundamentals/code-analysis/quality-rules/ca2361) — добавлены правила для DataSet и DataTable.
- [CA2362. Ненадежные данные DataSet или DataTable в автоматически созданном сериализуемом типе могут быть уязвимыми для атак удаленного выполнения кода](/dotnet/fundamentals/code-analysis/quality-rules/ca2362) — добавлены правила для DataSet и DataTable.
- [IL3000. Не используйте путь к файлу сборки при публикации в виде одного файла](/dotnet/fundamentals/code-analysis/quality-rules/il3000) — добавлена документация по IL3000.
- [IL3001. Не используйте путь к файлу сборки при публикации в виде одного файла](/dotnet/fundamentals/code-analysis/quality-rules/il3001) — добавлена документация по IL3001.

**Обновленные возможности**

- [CA1002. Не предоставляйте универсальные списки](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1046. Не перегружайте оператор равенства для ссылочных типов](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1307. Определите StringComparison для ясности](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) — добавлена документация по CA1310 и обновлена документация по CA1307.
- [CA1700. Не включайте в имя значений перечисления слово reserved](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1707. Идентификаторы не должны содержать символы подчеркивания](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1822. Пометьте элементы как статические](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) — добавлен раздел о настройке для использования контактной зоны API.
- [CA2351. Убедитесь, что входные данные DataSet.ReadXml() являются доверенными](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) — добавлены правила для DataSet и DataTable.
- [Установите сторонние анализаторы](../code-quality/install-roslyn-analyzers.md) — изменены структура и заголовки в документации по анализу кода.

### <a name="containers"></a>Контейнеры

**Обновленные статьи**

- [Развертывание контейнера ASP.NET в реестр контейнеров из Visual Studio](../containers/hosting-web-apps-in-docker.md) — обновление инструментов для контейнера для пользовательского интерфейса публикации Visual Studio 16.7.
- [Начало работы со Средствами Visual Studio для Kubernetes](../containers/bridge-to-kubernetes.md) — руководство по Kubernetes: добавление шагов для удаления.

### <a name="deployment"></a>Развертывание

**Новые статьи**

- [Расширение проектов Visual Studio Installer и .NET Core 3.1](../deployment/installer-projects-net-core.md) — создание новой страницы справки о возможностях установщика проектов .NET Core 3.1.

**Обновленные статьи**

- [Развертывание приложения в папке, IIS, Azure или другом расположении](../deployment/deploying-applications-services-and-components-resources.md) — обновления развертывания.
- [Документация по развертыванию Visual Studio](../deployment/index.yml) — обновления развертывания.

### <a name="extensibility"></a>Расширение среды

**Обновленные статьи**
- [Подтипы проектов](../extensibility/internals/project-subtypes.md) — исправлены отступы для элементов списка.
- [Справочник по значениям цветов для Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) — AB#1759333: исправлены отсутствующие заголовки столбцов.

### <a name="get-started"></a>Начало работы

**Обновленные статьи**

- [Шаг 5. Развертывание приложения ASP.NET Core в Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) — обновления видеоруководства по новому пользовательскому интерфейсу Подключенных служб.

### <a name="ide"></a>IDE

**Новые статьи**

- [Изменение клавиши справки F1 в Visual Studio](./not-in-toc/change-f1-help-key.md) — рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Справка по клавише F1 для текстового редактора](./not-in-toc/default-f1-text-editor.md) —рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Преобразование `typeof` в `nameof`](./reference/convert-typeof-to-nameof.md) — рефакторинг страницы, посвященной преобразованию typeof в nameof.
- [Упрощение выражения LINQ](./reference/simplify-linq-expression.md) — рефакторинг страницы, посвященной упрощению выражения LINQ.

**Обновленные статьи**

- [Настройка макетов окон в Visual Studio](./customizing-window-layouts-in-visual-studio.md) — добавлены сведения о вертикальных вкладках документов с моникерами в статье о настройке макетов окон.
- [Как сообщить о проблеме с Visual Studio или Visual Studio Installer](./how-to-report-a-problem-with-visual-studio.md)
  - Добавлены дополнительные сведения о NMI.
  - Переработана страница со сведениями о том, как отправить сообщение о проблеме.
- [Справка F1](./not-in-toc/default.md) —рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"](./reference/autorecover-environment-options-dialog-box.md) — добавлены сведения о обновленных расположениях файлов автосохранения.
- ["Параметры", "Текстовый редактор", Basic (Visual Basic), "Дополнительно"](./reference/options-text-editor-basic-visual-basic.md) — добавлена базовая документация по встроенным указаниям имен параметров.
- ["Параметры", "Текстовый редактор", C#, "Дополнительно"](./reference/options-text-editor-csharp-advanced.md) — добавлена базовая документация по встроенным указаниям имен параметров.
- [Советы и рекомендации по улучшению работы Visual Studio](./visual-studio-performance-tips-and-tricks.md) — добавлены сведения об отключении режима карты и переноса по словам.
- [Новые возможности Visual Studio 2019](./whats-new-visual-studio-2019.md) — обновлены сведения о новых возможностях общедоступной версии Visual Studio 2019 16.7.

### <a name="rtvs"></a>RTVS

**Обновленные статьи**

- [Работа с SQL Server и R](../rtvs/integrating-sql-server-with-r.md) — в таблицы включены заголовки столбцов.

## <a name="july-2020"></a>Июль 2020 г.
### <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1417. Не используйте в строковых параметрах `OutAttribute` для P/Invoke](/dotnet/fundamentals/code-analysis/quality-rules/ca1417). Добавлена документация по CA1417.
- [CA1805. Не делайте лишних инициализаций.](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) Добавлена документация по CA1805.
- [CA1836. Отдавайте предпочтение IsEmpty перед Count (при наличии)](/dotnet/fundamentals/code-analysis/quality-rules/ca1836). Добавлена документация по CA1836 (предпочтение IsEmpty вместо Count)
- [CA2016. Переадресуйте параметр CancellationToken методам, которые его принимают](/dotnet/fundamentals/code-analysis/quality-rules/ca2016). Документ CA2016 (переадресация параметра CancellationToken методам, которые его принимают).
- [CA2350. Убедитесь, что входные данные DataTable.ReadXml() являются доверенными](/dotnet/fundamentals/code-analysis/quality-rules/ca2350) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2351. Убедитесь, что входные данные DataSet.ReadXml() являются доверенными](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2352. Ненадежные данные DataSet или DataTable в сериализуемом типе могут быть уязвимыми для атак удаленного выполнения кода](/dotnet/fundamentals/code-analysis/quality-rules/ca2352) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2353. Ненадежные данные DataSet или DataTable в сериализуемом типе](/dotnet/fundamentals/code-analysis/quality-rules/ca2353) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2354. Ненадежные данные DataSet или DataTable в графе десериализованных объектов могут быть уязвимыми для атаки удаленного выполнения кода](/dotnet/fundamentals/code-analysis/quality-rules/ca2354) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2355. Ненадежные данные DataSet или DataTable в графе десериализованных объектов](/dotnet/fundamentals/code-analysis/quality-rules/ca2355) (базовая документация по правилам десериализации DataSet и DataTable).
- [CA2356. Ненадежные данные DataSet или DataTable в графе десериализованных веб-объектов](/dotnet/fundamentals/code-analysis/quality-rules/ca2356) (базовая документация по правилам десериализации DataSet и DataTable).

### <a name="containers"></a>Контейнеры

**Новые статьи**

- [Настройка функции "Локальный процесс с Kubernetes"](../containers/configure-bridge-to-kubernetes.md) (конфигурация YAML для локального процесса с Kubernetes).
- [Использование Локального процесса с Kubernetes (предварительная версия)](../containers/bridge-to-kubernetes.md) — перенос Dev Spaces.
- [Принцип работы функции "Локальный процесс с Kubernetes"](../containers/overview-bridge-to-kubernetes.md)
  - Локальный процесс для Kubernetes. Добавлен раздел по маршрутизации.
  - Перенос Dev Spaces.

### <a name="cross-platform"></a>Кроссплатформенные

**Обновленные статьи**

- [Журнал изменений (инструменты Visual Studio для Unity, Windows)](/gamedev/unity/change-log-visual-studio-tools-for-unity.md), версия журнала изменений VSTU увеличена до 4.7.1.0
- [Журнал изменений (инструменты Visual Studio для Unity, Mac)](/gamedev/unity/change-log-visual-studio-tools-for-unity-mac.md), версия журнала изменений VSTUM увеличена до 2.7.1.0

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