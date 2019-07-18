---
title: Уровень совместимости базы данных
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9115e675c43e04496712784371ac2301ef7c2f8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566694"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Совместимые системы баз данных для Visual Studio

Для разработки приложений, подключенных к данных, в Visual Studio, обычно установка системы базы данных на локальном компьютере разработки и затем развернуть приложение и база данных в рабочей среде, когда они будут готовы. Visual Studio устанавливает SQL Server Express LocalDB на локальном компьютере как часть **хранение и обработка данных** рабочей нагрузки. Этот экземпляр LocalDB можно использовать для разработки приложений, подключенных к данным, быстро и легко.

Для системы баз данных могут быть недоступны в приложениях .NET и должен отображаться в Visual Studio данные средства windows он должен иметь поставщик данных ADO.NET. Поставщик должен поддерживать Entity Framework в частности в том случае, если вы планируете использовать модели EDM в приложении .NET. Многие поставщики, предлагается через диспетчер пакетов NuGet или в Visual Studio Marketplace.

При использовании API хранилищ Azure, установите эмуляторы хранилища Azure на локальном компьютере во время разработки Чтобы избежать расходов, пока вы не будете готовы к развертыванию в рабочей среде. Дополнительные сведения см. в разделе [использование эмулятора хранилища Azure для разработки и тестирования](/azure/storage/common/storage-use-emulator).

В следующем списке приведены некоторые из наиболее популярных систем базы данных, которые могут быть использованы в проектах Visual Studio. Список не является исчерпывающим. Перечень сторонних поставщиков, предлагающих поставщиков данных ADO.NET, которые позволяют глубокая интеграция с помощью инструментов Visual Studio, см. в разделе [поставщиков данных ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server — база данных Microsoft флагманское предложение. SQL Server 2016 предоставляет рекордной производительности, повышенной безопасности и функционально насыщенные, интегрированные отчетов и аналитики. Он поставляется в различных выпусках, предназначенные для разных случаев использования: с высокой степенью масштабируемости, высокой производительности бизнес-аналитики, чтобы использовать на одном компьютере. SQL Server Express — это полнофункциональный выпуск SQL Server, разработанных специально для распространение и внедрение.  LocalDB — это упрощенная версия SQL Server Express, которая не требует настройки и выполняется в процессе приложения. Вы можете скачать одного или обоих этих продуктов из [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Во многих примерах SQL в этом разделе используется SQL Server LocalDB. SQL Server Management Studio (SSMS) — это приложение управления автономную базу данных, который больше функций, чем доступно в обозревателе объектов SQL Server Visual Studio. По предыдущей ссылке можно получить SSMS.

## <a name="oracle"></a>Oracle

Можно загрузить платную или бесплатную версию базы данных Oracle из [сетевой технологии Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) страницы. Для поддержки времени разработки для Entity Framework и адаптеров таблиц, вам потребуется [Oracle Developer tools для Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Другие официальные продукты Oracle, включая Oracle Instant Client, доступны через диспетчер пакетов NuGet. Можно загрузить образец схем Oracle, следуя инструкциям в [электронной документации Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL — это система популярных СУБД с открытым кодом, который широко используется в организациях и веб-сайтов. Файлы для загрузки MySQL, MySQL для Visual Studio и связанных продуктов находятся на [MySQL в Windows](http://www.mysql.com/why-mysql/windows/). Третьим сторонам предложения различных расширений Visual Studio и управления автономного приложения для MySQL. Вы можете просмотреть предложения в диспетчере пакетов NuGet (**средства** > **диспетчер пакетов NuGet** > **управление пакетами NuGet для решения**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL — это система бесплатно, открытый объект реляционной базы данных. Чтобы установить его на Windows, его можно скачать из [страницу загрузки PostgreSQL](http://www.postgresql.org/download/windows/). Можно также создать PostgreSQL из исходного кода. Эта система core PostgreSQL предоставляет интерфейс для языка C. Многие сторонние поставщики предоставляют пакеты NuGet для использования PostgreSQL из приложений .NET. Вы можете просмотреть предложения в диспетчере пакетов NuGet (**средства** > **диспетчер пакетов NuGet** > **управление пакетами NuGet для решения**) . Возможно, самым популярным пакетом обеспечивается [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite — это внедренные обработчик базы данных SQL, который выполняется в процессе приложения. Его можно загрузить из [страницу загрузки SQLite](http://www.sqlite.org/download.html). Также доступны многие сторонние пакеты NuGet, для SQLite. Вы можете просмотреть предложения в диспетчере пакетов NuGet (**средства** > **диспетчер пакетов NuGet** > **управление пакетами NuGet для решения**) .

## <a name="firebird"></a>Firebird

Firebird — это система базы данных SQL открытым исходным кодом. Его можно загрузить из [страницу загрузки Firebird](http://firebirdsql.org/en/downloads/). Поставщик данных ADO.NET доступен через диспетчер пакетов NuGet.

## <a name="see-also"></a>См. также

- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Определение версии и выпуска системы SQL Server и ее компонентов](http://support.microsoft.com/kb/321185)