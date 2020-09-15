---
title: 'Документация по Visual Studio. Изменения в выпуске за август 2020 г. '
titleSuffix: ''
description: Обновления документации по Visual Studio за август 2020 г.
ms.date: 09/02/2020
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
ms.openlocfilehash: 4364bd62ac19be958632b8cb2dbbe907013e8a70
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402248"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Документация по Visual Studio. Изменения в выпуске за август 2020 г.

Узнайте, что изменилось в документации по Visual Studio за август 2020 г. В этой статье перечислены основные изменения, внесенные в документацию в течение этого периода. Сведения об изменениях за предыдущие месяцы см. в [сводке по изменениям](whats-new-visual-studio-docs-history.md).

## <a name="azure"></a>Azure

**Новые статьи**

- [Добавление Azure Application Insights с использованием Подключенных служб Visual Studio](/visualstudio/azure/azure-app-insights-add-connected-service) — Подключенные службы для VS 2019 16.7
- [Добавление Кэша Azure для Redis с использованием Подключенных служб Visual Studio](/visualstudio/azure/azure-cache-for-redis-add-connected-service) — Подключенные службы для VS 2019 16.7
- [Добавление Azure Cosmos DB в приложение с использованием Подключенных служб Visual Studio](/visualstudio/azure/azure-cosmosdb-add-connected-service) — Подключенные службы для VS 2019 16.7
- [Добавление Azure SignalR с использованием Подключенных служб Visual Studio](/visualstudio/azure/azure-signalr-add-connected-service) — Подключенные службы для VS 2019 16.7
- [Добавление подключения к Базе данных SQL Azure](/visualstudio/azure/azure-sql-database-add-connected-service) — Подключенные службы для VS 2019 16.7

**Обновленные статьи**

- [Добавление хранилища Azure с использованием подключенных служб Visual Studio](/visualstudio/azure/vs-azure-tools-connected-services-storage)
  - Подключенные службы для VS 2019 16.7.
  - Статья о подключенных службах службы хранилища Azure: обновление пользовательского интерфейса обновления и поддерживаемых типов проектов.

## <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1310. Определите StringComparison для правильности](/visualstudio/code-quality/ca1310) — добавлена документация по CA1310 и обновлена документация по CA1307.
- [CA1837. Используйте Environment.ProcessId вместо Process.GetCurrentProcess().Id](/visualstudio/code-quality/ca1837) — документация по CA1837.
- [CA1838. Не используйте строковые параметры `StringBuilder` для P/Invoke](/visualstudio/code-quality/ca1838) — добавлена документация по CA1838.
- [CA2008. Не создавайте задачи без передачи TaskScheduler](/visualstudio/code-quality/ca2008) — добавлена документация по CA2008.
- [CA2249. Попробуйте использовать String.Contains вместо String.IndexOf](/visualstudio/code-quality/ca2249) — добавлена документация по СА2249.
- [CA2361. Убедитесь, что автоматически сформированный класс, который содержит DataSet.ReadXml(), не используется с ненадежными данными](/visualstudio/code-quality/ca2361) — добавлены правила для DataSet и DataTable.
- [CA2362. Ненадежные данные DataSet или DataTable в автоматически созданном сериализуемом типе могут быть уязвимыми для атак удаленного выполнения кода](/visualstudio/code-quality/ca2362) — добавлены правила для DataSet и DataTable.
- [IL3000. Не используйте путь к файлу сборки при публикации в виде одного файла](/visualstudio/code-quality/il3000) — добавлена документация по IL3000.
- [IL3001. Не используйте путь к файлу сборки при публикации в виде одного файла](/visualstudio/code-quality/il3001) — добавлена документация по IL3001.

**Обновленные возможности**

- [CA1002. Не предоставляйте универсальные списки](/visualstudio/code-quality/ca1002) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1046. Не перегружайте оператор равенства для ссылочных типов](/visualstudio/code-quality/ca1046) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1307. Определите StringComparison для ясности](/visualstudio/code-quality/ca1307) — добавлена документация по CA1310 и обновлена документация по CA1307.
- [CA1700. Не включайте в имя значений перечисления слово reserved](/visualstudio/code-quality/ca1700) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1707. Идентификаторы не должны содержать символы подчеркивания](/visualstudio/code-quality/ca1707) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1822. Пометьте элементы как статические](/visualstudio/code-quality/ca1822) — добавлен раздел о настройке для использования контактной зоны API.
- [CA2351. Убедитесь, что входные данные DataSet.ReadXml() являются доверенными](/visualstudio/code-quality/ca2351) — добавлены правила для DataSet и DataTable.
- [Установите сторонние анализаторы](/visualstudio/code-quality/install-roslyn-analyzers) — изменены структура и заголовки в документации по анализу кода.

## <a name="containers"></a>Контейнеры

**Обновленные статьи**

- [Развертывание контейнера ASP.NET в реестр контейнеров из Visual Studio](/visualstudio/containers/hosting-web-apps-in-docker) — обновление инструментов для контейнера для пользовательского интерфейса публикации Visual Studio 16.7.
- [Начало работы со Средствами Visual Studio для Kubernetes](/visualstudio/containers/tutorial-kubernetes-tools) — руководство по Kubernetes: добавление шагов для удаления.

## <a name="deployment"></a>Развертывание

**Новые статьи**

- [Расширение проектов Visual Studio Installer и .NET Core 3.1](/visualstudio/deployment/installer-projects-net-core) — создание новой страницы справки о возможностях установщика проектов .NET Core 3.1.

**Обновленные статьи**

- [Развертывание приложения в папке, IIS, Azure или другом расположении](/visualstudio/deployment/deploying-applications-services-and-components-resources) — обновления развертывания.
- [Документация по развертыванию Visual Studio](/visualstudio/deployment/index) — обновления развертывания.

## <a name="extensibility"></a>Расширение среды

**Обновленные статьи**
- [Подтипы проектов](/visualstudio/extensibility/internals/project-subtypes) — исправлены отступы для элементов списка.
- [Справочник по значениям цветов для Visual Studio](/visualstudio/extensibility/ux-guidelines/color-value-reference-for-visual-studio) — AB#1759333: исправлены отсутствующие заголовки столбцов.

## <a name="get-started"></a>Начало работы

**Обновленные статьи**

- [Шаг 5. Развертывание приложения ASP.NET Core в Azure](/visualstudio/get-started/csharp/tutorial-aspnet-core-ef-step-05) — обновления видеоруководства по новому пользовательскому интерфейсу Подключенных служб.

## <a name="ide"></a>IDE

**Новые статьи**

- [Изменение клавиши справки F1 в Visual Studio](/visualstudio/ide/not-in-toc/change-f1-help-key) — рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Справка по клавише F1 для текстового редактора](/visualstudio/ide/not-in-toc/default-f1-text-editor) —рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Преобразование `typeof` в `nameof`](/visualstudio/ide/reference/convert-typeof-to-nameof) — рефакторинг страницы, посвященной преобразованию typeof в nameof.
- [Упрощение выражения LINQ](/visualstudio/ide/reference/simplify-linq-expression) — рефакторинг страницы, посвященной упрощению выражения LINQ.

**Обновленные статьи**

- [Настройка макетов окон в Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio) — добавлены сведения о вертикальных вкладках документов с моникерами в разделе о настройке макетов окон.
- [Как сообщить о проблеме с Visual Studio или Visual Studio Installer](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
  - Добавлены дополнительные сведения о NMI.
  - Переработана страница со сведениями о том, как отправить сообщение о проблеме.
- [Справка F1](/visualstudio/ide/not-in-toc/default) —рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"](/visualstudio/ide/reference/autorecover-environment-options-dialog-box) — добавлены сведения о обновленных расположениях файлов автосохранения.
- ["Параметры", "Текстовый редактор", Basic (Visual Basic), "Дополнительно"](/visualstudio/ide/reference/options-text-editor-basic-visual-basic) — добавлена базовая документация по встроенным указаниям имен параметров.
- ["Параметры", "Текстовый редактор", C#, "Дополнительно"](/visualstudio/ide/reference/options-text-editor-csharp-advanced) — добавлена базовая документация по встроенным указаниям имен параметров.
- [Советы и рекомендации по улучшению работы Visual Studio](/visualstudio/ide/visual-studio-performance-tips-and-tricks) — добавлены сведения об отключении режима карты и переноса по словам.
- [Новые возможности Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019) — обновлены сведения о новых возможностях общедоступной версии Visual Studio 2019 16.7.

## <a name="rtvs"></a>RTVS

**Обновленные статьи**

- [Работа с SQL Server и R](/visualstudio/rtvs/integrating-sql-server-with-r) — в таблицы включены заголовки столбцов.

## <a name="community-contributors"></a>Участники сообщества

Указанные ниже пользователи в течение этого периода внесли свой вклад в улучшение документации по Visual Studio. Спасибо! Сведения о том, как вносить изменения в документацию по Visual Studio, вы найдете в [руководстве для участников](https://docs.microsoft.com/contribute/).

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG) — Алекс Блек (Alex Black) (11)
- [Youssef1313](https://github.com/Youssef1313) — Юссеф Виктор (Youssef Victor) (8)
- [hyoshioka0128](https://github.com/hyoshioka0128) — Хироси Йосиока (Hiroshi Yoshioka) (3)
- [AstroChoco](https://github.com/AstroChoco) — Киан Лу (Qian Lu; Chocolate) (1)
- [athyunnath](https://github.com/athyunnath) — Атьюннас Элети (Athyunnath Eleti) (1)
- [caro-oviedo](https://github.com/caro-oviedo) — Каро Овиедо (Caro Oviedo) (1)
- [Evangelink](https://github.com/Evangelink) — Амаури Леве ( Amaury Levé) (1)
- [jethas-bennettjones](https://github.com/jethas-bennettjones) — Шафик Джета (Shafiq Jetha) (1)
- [nebuk89](https://github.com/nebuk89) — Бен Де Ст Пер-Готч (Ben De St Paer-Gotch) (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov) — Петр Куликов (1)
- [riQQ](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger) — Тимо Корнелиус Мецгер (Timo Cornelius Metzger) (1)
- [weitzhandler](https://github.com/weitzhandler) — Шимми (Shimmy) (1)