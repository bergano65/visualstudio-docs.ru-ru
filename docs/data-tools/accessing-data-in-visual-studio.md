---
title: "Доступ к данным в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: c3777249948ba4be917de4ec6c139e7a15bce0a7
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="accessing-data-in-visual-studio"></a>Доступ к данным в Visual Studio

В Visual Studio можно создавать приложения, которые подключаются к данным в практически в любой базе данных продукта или услуги, в любом формате, в любом месте — на локальном компьютере, в локальной сети или в public, private или гибридного облака.

Для приложений на языке JavaScript, Python, PHP, Ruby или C++ можно подключиться к данным, как-то еще, используя получение библиотек и кода. Для приложений .NET Visual Studio предоставляет средства, которые можно использовать для просмотра источников данных, создание модели объектов для хранения и управления данными в памяти и привязки данных к пользовательскому интерфейсу. Microsoft Azure предоставляет пакеты SDK для .NET, Java, Node.js, PHP, Python, Ruby и мобильных приложений и средств в Visual Studio для подключения к службе хранилища Azure.

В следующих списках приведены лишь некоторые из многих системах базы данных и хранилища, которые можно использовать из Visual Studio. [Microsoft Azure](https://azure.microsoft.com/) предложения — службы данных, которые включают все Подготовка и администрирование базового хранилища данных.  [Средства Azure для Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) — это необязательный компонент, который позволяет работать с хранилищами данных Azure непосредственно из Visual Studio. Большинство других SQL и NoSQL базы данных продуктов, которые перечислены здесь может размещаться на локальном компьютере, в локальной сети или в Microsoft Azure на виртуальной машине. В этом сценарии вы несете ответственность за управление самой базы данных.

**Microsoft Azure**

||||
|-|-|-|
|База данных SQL|DocumentDB|Хранилища (большие двоичные объекты, очереди, таблицы файлов)|
|Хранилище данных SQL|База данных SQL Server Stretch|StorSimple|

И многое другое!

**SQL**

||||
|-|-|-|
|SQL Server 2005 2016, включая экспресс-выпуск и LocalDB|Обеспечению фрагмента Firebird фильма|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

И многое другое!

**NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|Данных|OrientDB|RavenDB|
|VelocityDB|||

И многое другое!

Многие поставщики баз данных и сторонних разработчиков поддерживают интеграции Visual Studio с пакетами NuGet. Предложения можно просмотреть на nuget.org или через диспетчер пакетов NuGet в Visual Studio (**средства** > **диспетчера пакетов NuGet** > **управление пакетами NuGet Пакетами для решения**). Другие продукты баз данных интегрируется с Visual Studio в качестве расширения. Можно просмотреть эти предложения в Visual Studio Marketplace, перейдя к **средства**, **расширения и обновления** и выбрав **Online** в левой области диалоговое окно. Дополнительные сведения см. в разделе [систем совместимых баз данных для Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Расширенная поддержка SQL Server 2005 прекращена с 12 апреля 2016 г. Нет никакой гарантии, что данных средств в Visual Studio 2015 и более поздних версий будет продолжать работать с SQL Server 2005 после этой даты. Дополнительные сведения см. в разделе [объявления окончания поддержки для SQL Server 2005](https://www.microsoft.com/server-cloud/products/sql-server-2005/).

## <a name="net-languages"></a>В языках .NET

Все .NET доступ к данным, включая в .NET Core основан на ADO.NET, набор классов, определяющий интерфейс для доступа к любой тип источника данных, реляционных и нереляционных. В Visual Studio есть несколько средств и конструкторов, которые работают с ADO.NET для подключения к базам данных, управление данными и пользователь получает данные. Документация в этом разделе описывается использование этих средств. Вы также можете программировать непосредственно на командных объектов ADO.NET. Дополнительные сведения о прямом вызове API-интерфейсы ADO.NET см. в разделе [ADO.NET](/dotnet/framework/data/adonet/index).

См. документацию доступа к данным непосредственно связаны с ASP.NET [работа с данными](http://www.asp.net/web-forms/overview/presenting-and-managing-data) на веб-сайте ASP.NET. Учебник по использованию платформы Entity Framework с ASP.NET MVC см. в разделе [Приступая к работе с Entity Framework 6 Code First MVC 5 с помощью](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Для доступа к службе хранилища Azure и другими службами Azure универсальных приложений для платформы Windows (UWP) в C# или Visual Basic можно использовать Microsoft Azure SDK для .NET. Класс Windows.Web.HttpClient разрешает взаимодействие с любой службы RESTful. Дополнительные сведения см. в разделе [подключение к HTTP-серверу с помощью Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Для хранения данных на локальном компьютере рекомендуется использовать SQLite, которая выполняется в том же процессе, что и приложение. Если необходим уровень объектно реляционного сопоставления (ORM), можно использовать Entity Framework. Дополнительные сведения см. в разделе [доступа к данным](https://msdn.microsoft.com/windows/uwp/data-access/index) в центре разработчиков Windows.

При подключении к службам Azure, необходимо загрузить последнюю версию [инструментов пакета Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Поставщики данных

Для базы данных, чтобы можно было использовать в ADO.NET, он должен иметь пользовательское *поставщика данных ADO.NET* или else должен предоставлять интерфейс ODBC или OLE DB. Корпорация Майкрософт предоставляет [список поставщиков данных ADO.NET](https://msdn.microsoft.com/data/dd363565) продуктов SQL Server, а также поставщиков ODBC и OLE DB.

### <a name="data-modeling"></a>Моделирование данных

В .NET у вас есть три варианта для моделирования и обработка данных в памяти после его получения из источника данных:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md)  
Технология Microsoft ORM. Его можно использовать для программирования реляционных данных как полноценные объекты .NET. Для новых приложений следует отдавать по умолчанию при необходимости модели. Он требует настраиваемую поддержку от базового поставщика ADO.NET.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
Объектно реляционного сопоставления предыдущих поколений. Он хорошо подходит для более сложных сценариев, но больше не находится в активной разработке.

[Наборы данных](../data-tools/dataset-tools-in-visual-studio.md)  
Самый старый из три технологии моделирования. Она предназначена главным образом для быстрой разработки приложений «форм на основе данных», в которых не обработки огромные объемы данных или выполнения сложных запросов или преобразования. Объект DataSet состоит из объектов DataTable и DataRow, логически гораздо больше, чем объекты .NET похожих объектов базы данных SQL. Для относительно простых приложений, основанных на источниках данных SQL наборов данных по-прежнему может быть хорошим выбором.

Нет необходимости использовать любой из этих технологий. В некоторых сценариях особенно в том случае, если важна производительность, можно просто использовать объект DataReader для чтения из базы данных и скопируйте нужные значения в объект коллекции, например, список\<T >.

## <a name="native-c"></a>Неуправляемый C++

Приложения C++, подключиться к SQL Server следует использовать [Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) в большинстве случаев. Если связанные серверы, то необходим OLE DB и, используйте [собственный клиент SQL Server](/sql/relational-databases/native-client/sql-server-native-client). Доступ к другим базам данных с помощью [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) или непосредственно драйверы OLE DB. ODBC — это текущий интерфейс стандартной базы данных, но большинство баз данных предоставляют пользовательские функции, которые недоступны через интерфейс ODBC. OLE DB — это устаревшая технология доступа к данным COM, который по-прежнему поддерживается, но не рекомендуется для новых приложений. Дополнительные сведения см. в разделе [доступ к данным в Visual C++](/cpp/data/data-access-in-cpp).

Использование служб REST программы C++ могут использовать [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Можно использовать программы C++, которые работают со службой хранилища Microsoft Azure [клиент хранилища Microsoft Azure](http://www.nuget.org/packages/wastorage).

Моделирование данных&mdash;Visual Studio не обеспечивают уровень ORM C++. [ODB](http://www.codesynthesis.com/products/odb/) — популярный ORM открытым исходным кодом для C++.

Дополнительные сведения о подключении к базам данных из приложений C++ см. в разделе [данных средств Visual Studio для C++](../data-tools/visual-studio-data-tools-for-cpp.md). Дополнительные сведения о технологиях доступа к данным прежних версий Visual C++ см. в разделе [доступа к данным](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript в Visual Studio](/scripting/javascript/javascript-language-reference) — полноправный язык для построения кросс платформенные приложения, приложения UWP, облачные службы, веб-сайтов и веб-приложений. Bower, Grunt, Gulp, npm и NuGet из среды Visual Studio можно использовать для установки избранные библиотек JavaScript и базам данных. Подключиться к хранилищу Azure и службам путем загрузки пакетов SDK из [веб-сайте Azure](https://azure.microsoft.com/). Edge.js — это библиотека, который подключается к источникам данных ADO.NET серверные JavaScript (Node.js).

## <a name="python"></a>Python

Установка [средства Python для Visual Studio](http://microsoft.github.io/PTVS/) вместе с вашей избранные платформы Python для создания приложений, CPython или IronPython (.NET). Средства Python для Visual Studio веб-сайта есть несколько учебников по подключению к данным, включая [Django и база данных SQL в Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django и MySQL в Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) и [Bottle и MongoDB на Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="related-topics"></a>См. также

[Данные, устройств и аналитика](https://msdn.microsoft.com/data-and-devices)  
Введение в интеллектуальный облака Майкрософт, включая Cortana Analytics Suite и поддержка Интернета вещей.

[Хранилище Microsoft Azure](https://azure.microCsoft.com/documentation/services/storage/)  
Описание хранилища Azure и создание приложений с помощью Azure BLOB-объектов, таблиц, очередей и файлов.

[База данных Azure SQL](https://azure.microsoft.com/documentation/services/sql-database/)  
Описывает, как подключиться к базе данных SQL Azure, реляционную базу данных в качестве службы.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)  
Описание средств, упрощающих конструктора, просмотр, тестирования и развертывания приложений, связанных данных и баз данных.

[ADO.NET](/dotnet/framework/data/adonet/index)  
Описание архитектуры ADO.NET и способов использования классов ADO.NET для управления данными приложения и взаимодействия с источниками данных и XML.

[ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)  
Описывает, как создавать приложения данные, которые позволяют разработчикам программировать в концептуальной модели, а не непосредственно к реляционной базе данных.

[Службы данных WCF 4.5](/dotnet/framework/data/wcf/index)  
Описывает использование [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] для развертывания служб данных в Интернете или интрасети, которые реализуют [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

[Данные в решениях Office](../vsto/data-in-office-solutions.md)  
Содержит ссылки на разделы, в которых объясняется работа с данными в решениях Office. Сюда входят сведения о схемо ориентированном программировании, кэшировании данных и доступа к данным на стороне сервера.

[Встроенный язык запросов LINQ](/dotnet/csharp/linq/)  
Описывает возможности запросов, встроенные в C# и Visual Basic и общей модели для запроса реляционных баз данных, документы XML, наборы данных и коллекции в памяти.

[Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)  
Описание работы с .NET Framework XML функции XML данные отладки XSLT и архитектура XML-запроса.

[XML-документы и данные](/dotnet/standard/data/xml/index)  
Здесь приводится обзор обширного и встроенного набора классов, предназначенных для работы с XML-документами и данными в .NET Framework.