---
title: Установка систем баз данных, средств и примеров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 091338e411369e40f19e028cd19b6cb2e697718c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299611"
---
# <a name="installing-database-systems-tools-and-samples"></a>Установка систем баз данных, средств и примеров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio сама по себе не содержит никаких систем баз данных, кроме используемых для внутренних целей. Для разработки подключенного к данным приложения в Visual Studio обычно необходимо установить систему базы данных на локальном компьютере разработки, а затем развернуть приложение и базу данных в рабочей среде, когда они будут готовы. Чтобы система базы данных была доступна из приложений .NET и была видима в окнах Visual Studio Data Tools, у нее должен быть поставщик данных ADO.NET. Поставщик должен специально поддерживать Entity Framework, если планируется использовать модели EDM в приложении .NET.     Многие поставщики предлагаются с помощью диспетчера пакетов NuGet или коллекции Visual Studio.

 Для разработки SQL убедитесь, что в Visual Studio установлен SQL Server Data Tools. Откройте меню **вид** . Если вы не видите обозреватель объектов SQL Server, перейдите на панель управления и измените Visual Studio. В установщике выберите **Microsoft SQL Server Data Tools**.

 Если вы используете API службы хранилища Azure, установите Эмуляторы хранения Azure на локальном компьютере во время разработки, чтобы избежать расходов, пока вы не будете готовы к развертыванию в рабочей среде. Дополнительные сведения см. в статье [Использование эмулятора хранения Azure для разработки и тестирования](https://azure.microsoft.com/documentation/articles/storage-use-emulator/).

 В следующем списке перечислены некоторые из наиболее популярных систем баз данных, которые можно использовать в проектах Visual Studio. Список не является исчерпывающим. Список сторонних поставщиков, предлагающих поставщиков данных ADO.NET, которые обеспечивают глубокую интеграцию с инструментами Visual Studio, см. в разделе [ADO.NET Data providers](https://msdn.microsoft.com/library/dd363565.aspx).

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server является предложением базы данных Microsoft Флагманское. SQL Server 2016 обеспечивает рекордную производительность, расширенную безопасность и многофункциональную интегрированную отчетность и аналитику. Он поставляется в различных выпусках, предназначенных для различных целей: от высокомасштабируемых и высокопроизводительных бизнес-аналитиков до использования на одном компьютере. SQL Server Express — это полнофункциональный выпуск SQL Server, предназначенный для распространения и внедрения.  LocalDB — это упрощенный выпуск SQL Server Express, который не требует настройки и выполняется в процессе приложения. Можно загрузить один или оба продукта со [страницы загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Во многих примерах SQL в этом разделе используется SQL Server LocalDB. SQL Server Management Studio (SSMS) — это изолированное приложение для управления базами данных, которое имеет больше функциональных возможностей, чем предоставлено в Visual Studio обозреватель объектов SQL Server. Для получения среды SSMS можно воспользоваться предыдущей ссылкой.

### <a name="oracle"></a>Oracle;
 Вы можете скачать платную или бесплатную версию базы данных Oracle с помощью [сетевой страницы технологии Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) . Чтобы обеспечить поддержку во время разработки для Entity Framework и адаптеров таблиц, вам потребуется [средства для разработчиков Oracle для Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Другие официальные продукты Oracle, включая мгновенный клиент Oracle, доступны через диспетчер пакетов NuGet.  Вы можете скачать образцы схем Oracle, следуя инструкциям в [электронной документации по Oracle](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

### <a name="mysql"></a>MySQL
 MySQL — это популярная система баз данных с открытым кодом, широко используемая на предприятиях и веб-сайтах. Загружаемые файлы для MySQL, MySQL для Visual Studio и связанных продуктов находятся в [MySQL в Windows](https://www.mysql.com/why-mysql/windows/).  Сторонние лица предлагают различные расширения Visual Studio и автономные приложения управления для MySQL. Вы можете просмотреть предложения в диспетчере пакетов NuGet (**инструменты**  >  **Диспетчер пакетов NuGet**  >  **Управление пакетами NuGet для решения**).

### <a name="postgresql"></a>PostgreSQL
 PostgreSQL — это бесплатная система реляционной базы данных с открытым исходным кодом. Чтобы установить его в Windows, можно скачать его со [страницы загрузки PostgreSQL](http://www.postgresql.org/download/windows/).  Можно также создать PostgreSQL из исходного кода.  Система PostgreSQL Core включает в себя интерфейс языка C. Многие сторонние лица предоставляют пакеты NuGet для использования PostgreSQL из приложений .NET.  Вы можете просмотреть предложения в диспетчере пакетов NuGet (**инструменты**  >  **Диспетчер пакетов NuGet**  >  **Управление пакетами NuGet для решения**). Возможно, самый популярный пакет предоставляется [npgsql.org](http://www.npgsql.org/).

### <a name="sqlite"></a>SQLite
 SQLite — это встроенное ядро СУБД SQL, которое работает в собственном процессе приложения. Его можно скачать на [странице загрузки SQLite](http://www.sqlite.org/download.html). Также доступны многие сторонние пакеты NuGet для SQLite. Вы можете просмотреть предложения в диспетчере пакетов NuGet (**инструменты**  >  **Диспетчер пакетов NuGet**  >  **Управление пакетами NuGet для решения**).

### <a name="firebird"></a>Firebird
 Firebird — это система баз данных SQL с открытым исходным кодом. Его можно загрузить на [странице загрузки Firebird](http://firebirdsql.org/en/downloads/). Поставщик данных ADO.NET доступен через диспетчер пакетов NuGet.

## <a name="see-also"></a>См. также
 [Как определить версию, выпуск и уровень обновления системы SQL Server и ее компонентов](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
