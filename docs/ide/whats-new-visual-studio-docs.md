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
ms.openlocfilehash: 2411299fbab6dfba8ced0f689bd33825b62614af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808985"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Документация по Visual Studio. Изменения в выпуске за август 2020 г.

Узнайте, что изменилось в документации по Visual Studio за август 2020 г. В этой статье перечислены основные изменения, внесенные в документацию в течение этого периода. Сведения об изменениях за предыдущие месяцы см. в [сводке по изменениям](whats-new-visual-studio-docs-history.md).

## <a name="azure"></a>Azure

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

## <a name="code-quality"></a>Качество кода

**Новые статьи**

- [CA1310. Определите StringComparison для правильности](../code-quality/ca1310.md) — добавлена документация по CA1310 и обновлена документация по CA1307.
- [CA1837. Используйте Environment.ProcessId вместо Process.GetCurrentProcess().Id](../code-quality/ca1837.md) — документация по CA1837.
- [CA1838. Не используйте строковые параметры `StringBuilder` для P/Invoke](../code-quality/ca1838.md) — добавлена документация по CA1838.
- [CA2008. Не создавайте задачи без передачи TaskScheduler](../code-quality/ca2008.md) — добавлена документация по CA2008.
- [CA2249. Попробуйте использовать String.Contains вместо String.IndexOf](../code-quality/ca2249.md) — добавлена документация по СА2249.
- [CA2361. Убедитесь, что автоматически сформированный класс, который содержит DataSet.ReadXml(), не используется с ненадежными данными](../code-quality/ca2361.md) — добавлены правила для DataSet и DataTable.
- [CA2362. Ненадежные данные DataSet или DataTable в автоматически созданном сериализуемом типе могут быть уязвимыми для атак удаленного выполнения кода](../code-quality/ca2362.md) — добавлены правила для DataSet и DataTable.
- [IL3000. Не используйте путь к файлу сборки при публикации в виде одного файла](../code-quality/il3000.md) — добавлена документация по IL3000.
- [IL3001. Не используйте путь к файлу сборки при публикации в виде одного файла](../code-quality/il3001.md) — добавлена документация по IL3001.

**Обновленные возможности**

- [CA1002. Не предоставляйте универсальные списки](../code-quality/ca1002.md) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1046. Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046.md) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1307. Определите StringComparison для ясности](../code-quality/ca1307.md) — добавлена документация по CA1310 и обновлена документация по CA1307.
- [CA1700. Не включайте в имя значений перечисления слово reserved](../code-quality/ca1700.md) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1707. Идентификаторы не должны содержать символы подчеркивания](../code-quality/ca1707.md) — добавлен раздел о настройке для использования контактной зоны API.
- [CA1822. Пометьте элементы как статические](../code-quality/ca1822.md) — добавлен раздел о настройке для использования контактной зоны API.
- [CA2351. Убедитесь, что входные данные DataSet.ReadXml() являются доверенными](../code-quality/ca2351.md) — добавлены правила для DataSet и DataTable.
- [Установите сторонние анализаторы](../code-quality/install-roslyn-analyzers.md) — изменены структура и заголовки в документации по анализу кода.

## <a name="containers"></a>Контейнеры

**Обновленные статьи**

- [Развертывание контейнера ASP.NET в реестр контейнеров из Visual Studio](../containers/hosting-web-apps-in-docker.md) — обновление инструментов для контейнера для пользовательского интерфейса публикации Visual Studio 16.7.
- [Начало работы со Средствами Visual Studio для Kubernetes](../containers/tutorial-kubernetes-tools.md) — руководство по Kubernetes: добавление шагов для удаления.

## <a name="deployment"></a>Развертывание

**Новые статьи**

- [Расширение проектов Visual Studio Installer и .NET Core 3.1](../deployment/installer-projects-net-core.md) — создание новой страницы справки о возможностях установщика проектов .NET Core 3.1.

**Обновленные статьи**

- [Развертывание приложения в папке, IIS, Azure или другом расположении](../deployment/deploying-applications-services-and-components-resources.md) — обновления развертывания.
- [Документация по развертыванию Visual Studio](../deployment/index.yml) — обновления развертывания.

## <a name="extensibility"></a>Расширение среды

**Обновленные статьи**
- [Подтипы проектов](../extensibility/internals/project-subtypes.md) — исправлены отступы для элементов списка.
- [Справочник по значениям цветов для Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) — AB#1759333: исправлены отсутствующие заголовки столбцов.

## <a name="get-started"></a>Начало работы

**Обновленные статьи**

- [Шаг 5. Развертывание приложения ASP.NET Core в Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) — обновления видеоруководства по новому пользовательскому интерфейсу Подключенных служб.

## <a name="ide"></a>IDE

**Новые статьи**

- [Изменение клавиши справки F1 в Visual Studio](./not-in-toc/change-f1-help-key.md) — рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Справка по клавише F1 для текстового редактора](./not-in-toc/default-f1-text-editor.md) —рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Преобразование `typeof` в `nameof`](./reference/convert-typeof-to-nameof.md) — рефакторинг страницы, посвященной преобразованию typeof в nameof.
- [Упрощение выражения LINQ](./reference/simplify-linq-expression.md) — рефакторинг страницы, посвященной упрощению выражения LINQ.

**Обновленные статьи**

- [Настройка макетов окон в Visual Studio](./customizing-window-layouts-in-visual-studio.md) — добавлены сведения о вертикальных вкладках документов с моникерами в разделе о настройке макетов окон.
- [Как сообщить о проблеме с Visual Studio или Visual Studio Installer](./how-to-report-a-problem-with-visual-studio.md)
  - Добавлены дополнительные сведения о NMI.
  - Переработана страница со сведениями о том, как отправить сообщение о проблеме.
- [Справка F1](./not-in-toc/default.md) —рефакторинг страницы, посвященной справке F1 по умолчанию.
- [Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"](./reference/autorecover-environment-options-dialog-box.md) — добавлены сведения о обновленных расположениях файлов автосохранения.
- ["Параметры", "Текстовый редактор", Basic (Visual Basic), "Дополнительно"](./reference/options-text-editor-basic-visual-basic.md) — добавлена базовая документация по встроенным указаниям имен параметров.
- ["Параметры", "Текстовый редактор", C#, "Дополнительно"](./reference/options-text-editor-csharp-advanced.md) — добавлена базовая документация по встроенным указаниям имен параметров.
- [Советы и рекомендации по улучшению работы Visual Studio](./visual-studio-performance-tips-and-tricks.md) — добавлены сведения об отключении режима карты и переноса по словам.
- [Новые возможности Visual Studio 2019](./whats-new-visual-studio-2019.md) — обновлены сведения о новых возможностях общедоступной версии Visual Studio 2019 16.7.

## <a name="rtvs"></a>RTVS

**Обновленные статьи**

- [Работа с SQL Server и R](../rtvs/integrating-sql-server-with-r.md) — в таблицы включены заголовки столбцов.

## <a name="community-contributors"></a>Участники сообщества

Указанные ниже пользователи в течение этого периода внесли свой вклад в улучшение документации по Visual Studio. Спасибо! Сведения о том, как вносить изменения в документацию по Visual Studio, вы найдете в [руководстве для участников](/contribute/).

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