---
title: Уровень совместимости базы данных Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3c8cffef6144c188fd5f53e504f6065c4e7d0c1d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="compatible-database-systems-for-visual-studio"></a>Базы данных, совместимой системы для Visual Studio

Для разработки приложения данные, подключенные в Visual Studio, обычно установка системы базы данных на локальном компьютере разработчика и разверните приложения и базы данных в рабочей среде по мере готовности. Visual Studio устанавливает SQL Server Express LocalDB на компьютере как часть **хранения и обработки данных** рабочей нагрузки. Этот экземпляр LocalDB полезно для разработки приложений, связанных данных.

Система базы данных должна быть доступна в приложениях .NET и должен отображаться в окнах инструментов Visual Studio данных должен иметь поставщик данных ADO.NET. Поставщик должен поддерживать Entity Framework специально в том случае, если вы планируете использовать модели EDM в приложении .NET. Многие поставщики предоставляются через диспетчер пакетов NuGet или с помощью Visual Studio Marketplace.

При использовании API-интерфейсов хранилища Azure, установите эмуляторов хранилища Azure на локальном компьютере во время разработки во избежание накладных расходов, пока вы не будете готовы к развертыванию в рабочей среде. Дополнительные сведения см. в разделе [использование эмулятора хранилища Azure для разработки и тестирования](/azure/storage/common/storage-use-emulator).

В следующем списке перечислены некоторые популярные систем баз данных, которые могут использоваться в проектах Visual Studio. Список не является исчерпывающим. Список сторонних поставщиков, предлагающих поставщиков данных ADO.NET, позволяющие тесная интеграция с помощью средств Visual Studio см. в разделе [поставщиков данных ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server является основной базой данных Microsoft предложения. SQL Server 2016 обеспечивает рекордной производительности, повышенной безопасности и обширную, интегрированную отчетов и аналитики. Он поставляется в различных выпусках, предназначенных для различных целей: от чрезвычайно масштабируемую и высокопроизводительную бизнес-аналитики, чтобы на одном компьютере. SQL Server Express является полнофункциональный выпуск SQL Server, адаптированные для распространения и внедрения.  LocalDB — это упрощенная версия SQL Server Express, которая не требует настройки и выполняется в процессе приложения. Вы можете загрузить один или оба продукты из [страницы загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Во многих примерах SQL в этом разделе используется SQL Server LocalDB. SQL Server Management Studio (SSMS) — это приложение управления изолированная база данных, с более широкими функциональными возможностями, чем описано в обозревателе объектов SQL Server Visual Studio. Среда SSMS можно получить из предыдущая ссылка.

## <a name="oracle"></a>Oracle

Можно загрузить платную или бесплатную версию базы данных Oracle из [сетевой технологии Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) страницы. Для поддержки времени разработки для Entity Framework и адаптеры таблиц TableAdapter, вам потребуется [Oracle Developer Tools для Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Другие официальные продуктах Oracle, включая клиент Oracle Instant Client, доступны через диспетчер пакетов NuGet.  Можно загрузить образец схемы Oracle, следуя инструкциям в разделе [электронной документации Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL — это система популярных базы данных с открытым исходным кодом, который широко применяется в организациях и веб-сайтов. Загружаемые файлы для MySQL MySQL для Visual Studio и связанные продукты имеют [MySQL в Windows](http://www.mysql.com/why-mysql/windows/).  Сторонние поставщики предлагают различные расширений Visual Studio и автономного управления приложениями для MySQL. Можно просмотреть предложения диспетчера пакетов NuGet (**средства** > **диспетчера пакетов NuGet** > **управление пакетами NuGet для решения**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL является реляционной СУБД свободного объектом с открытым исходным кодом. Чтобы установить его в Windows, его можно загрузить из [страницы загрузки PostgreSQL](http://www.postgresql.org/download/windows/).  Можно также создать PostgreSQL из исходного кода.  Основная система PostgreSQL включает интерфейс языка C. Многие сторонние поставщики предоставляют пакеты NuGet для использования в приложениях .NET PostgreSQL.  Можно просмотреть предложения диспетчера пакетов NuGet (**средства** > **диспетчера пакетов NuGet** > **управление пакетами NuGet для решения**) . Возможно наиболее популярных пакетов обеспечивается [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite — это внедренные ядро базы данных SQL, выполняется в процессе приложения. Его можно загрузить из [страницы загрузки SQLite](http://www.sqlite.org/download.html). Также доступны многие сторонние пакеты NuGet SQLite. Можно просмотреть предложения диспетчера пакетов NuGet (**средства** > **диспетчера пакетов NuGet** > **управление пакетами NuGet для решения**) .

## <a name="firebird"></a>Firebird

Обеспечению фрагмента Firebird фильма — это система баз данных SQL открытым исходным кодом. Его можно загрузить из [страницы загрузки обеспечению фрагмента Firebird фильма](http://firebirdsql.org/en/downloads/). Поставщик данных ADO.NET доступен через диспетчер пакетов NuGet.

## <a name="see-also"></a>См. также

[Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Как определить версию и выпуск SQL Server и его компонентов](http://support.microsoft.com/kb/321185)