---
title: Доступ к данным и средства
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 7bd87013245bd1c9a28ea093433687009f9c35e8
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484151"
---
# <a name="access-data-in-visual-studio"></a>Доступ к данным в Visual Studio

В Visual Studio можно создавать приложения, которые подключаются к данным в практически любого продукта базы данных или службы, в любом формате, в любом месте — на локальном компьютере, на локальной сети или в общедоступные, частные и гибридные облака.

Для приложений на JavaScript, Python, PHP, Ruby или C++ можно подключаться к данным, как это сделать что-нибудь еще, получение библиотеки и написания кода. Для приложений .NET Visual Studio предоставляет средства, которые можно использовать для исследования источники данных и создавать модели объектов для хранения и обработки данных в памяти и привязка данных к пользовательскому интерфейсу. Microsoft Azure предоставляет пакеты SDK для .NET, Java, Node.js, PHP, Python, Ruby и мобильных приложений и средств в Visual Studio для подключения к службе хранилища Azure.

В следующих списках приведены лишь некоторые из многих системах базы данных и хранилища, которые могут быть использованы из Visual Studio. [Microsoft Azure](https://azure.microsoft.com/) предложения — это службы данных, которые включают все подготовки и администрирования из базового хранилища данных. **Разработки Azure** рабочей нагрузки в [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) позволяет работать с хранилищами данных Azure непосредственно из Visual Studio.

![Рабочая нагрузка "Разработка для Azure"](media/azure-development-workload.png)

Большинство других SQL и NoSQL базы данных продуктов, которые перечислены здесь может размещаться на локальном компьютере, в локальной сети, а также в Microsoft Azure на виртуальной машине. Если она размещается на виртуальной машине Microsoft Azure, вы несете ответственность за управление самой базы данных.

**Microsoft Azure**

- База данных SQL
- Azure Cosmos DB
- Хранилища (большие двоичные объекты, таблицы, очереди, файлы)
- Хранилище данных SQL
- SQL Server Stretch Database
- StorSimple
- И многое другое!

**SQL**

- SQL Server 2005 – 2016 (включая Express и LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- И многое другое!

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- Данных
- OrientDB |
- RavenDB
- VelocityDB
- И многое другое!

Многими поставщиками базы данных и третьим сторонам поддерживается интеграция с Visual Studio, пакеты NuGet. Вы можете изучить предложения на сайте nuget.org или через диспетчер пакетов NuGet в Visual Studio (**средства** > **диспетчер пакетов NuGet** > **управление пакетами NuGet Пакетами для решения**). Другие продукты баз данных интеграции с Visual Studio в качестве расширения. Эти предложения в Visual Studio Marketplace можно просмотреть, перейдя по адресу **средства**, **расширения и обновления** и выбрав **Online** в левой области диалоговое окно. Дополнительные сведения см. в разделе [совместимые системы баз данных для Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Расширенная поддержка SQL Server 2005 закончилась 12 апреля 2016 г. Нет никакой гарантии, что данные средства в Visual Studio 2015 и более поздних версий будет продолжать работать с SQL Server 2005, после этой даты. Дополнительные сведения см. в разделе [end-of-support объявление о выпуске для SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Языки .NET

Все .NET доступ к данным, включая в .NET Core основан на ADO.NET, набор классов, определяющий интерфейс для доступа к любой тип источника данных, реляционных и нереляционных. Visual Studio предоставляет несколько средств и конструкторов, которые работают с ADO.NET для подключения к базам данных, обработки данных и представления данных пользователю. Документация в этом разделе описывается, как использовать эти средства. Также можно запрограммировать напрямую с объектами команды ADO.NET. Дополнительные сведения о прямого вызова API-интерфейсы ADO.NET, см. в разделе [ADO.NET](/dotnet/framework/data/adonet/index).

Для доступа к данным документацией, относящейся к ASP.NET, см. в разделе [работа с данными](https://www.asp.net/web-forms/overview/presenting-and-managing-data) на веб-сайте ASP.NET. Учебник по использованию Entity Framework с ASP.NET MVC, см. в разделе [Приступая к работе с Entity Framework 6 Code First с помощью MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Универсальные приложения платформы Windows (UWP) в C# или Visual Basic можно использовать Microsoft Azure SDK для .NET для доступа к службе хранилища Azure и других служб Azure. Класс Windows.Web.HttpClient обеспечивает взаимодействие с любой службы RESTful. Дополнительные сведения см. в разделе [способ подключения к серверу HTTP, с помощью Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Для хранения данных на локальном компьютере рекомендуется использовать SQLite, которая выполняется в том же процессе, что и приложение. Если к слою объектно реляционного сопоставления (ORM) требуется, можно использовать Entity Framework. Дополнительные сведения см. в разделе [доступ к данным](/windows/uwp/data-access/index) в центре разработчиков Windows.

При подключении к службам Azure, необходимо загрузить последнюю версию [инструментов пакета Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Поставщики данных

Для базы данных должно использоваться в ADO.NET, он должен иметь пользовательский *поставщика данных ADO.NET* или else должны предоставлять интерфейс ODBC или OLE DB. Корпорация Майкрософт предоставляет [список поставщиков данных ADO.NET](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) продуктов SQL Server, а также поставщиков ODBC и OLE DB.

### <a name="data-modeling"></a>Моделирование данных

В .NET у вас есть три варианта для моделирования и работы с данными в памяти после ее получения из источника данных:

[Платформа Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) предпочтительной технологией Microsoft ORM. Его можно использовать для программирования реляционных данных как объекты .NET первичного класса. Для новых приложений это должен быть первый вариант по умолчанию, при необходимости модель. Он требует настраиваемую поддержку от базового поставщика ADO.NET.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) объектно реляционным модулем сопоставления предыдущих поколений. Он хорошо подходит для более сложных сценариев, но больше не находится в активной разработке.

[Наборы данных](../data-tools/dataset-tools-in-visual-studio.md) самый старый из трех технологий моделирования. Она предназначена в первую очередь для быстрой разработки приложений «формы поверх данных», в которых не обработки огромные объемы данных или выполнения сложных запросов или преобразования. Объект DataSet состоит из объектов DataTable и DataRow, логически похожих объектов базы данных SQL гораздо больше, чем объекты .NET. Для относительно простых приложений, основанных на источниках данных SQL наборов данных может быть хорошим выбором.

Нет никаких требований к использованию в любой из этих технологий. В некоторых сценариях, особенно в том случае, если важна производительность, можно просто использовать объект DataReader для чтения из базы данных и скопируйте необходимые значения в объект коллекции, такой как список\<T >.

## <a name="native-c"></a>Неуправляемый C++

Приложения C++, которые подключаются к SQL Server, должны использовать [Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) в большинстве случаев. Серверы, если не связан, а затем OLE DB необходим и для этого используется [собственный клиент SQL Server](/sql/relational-databases/native-client/sql-server-native-client). Доступ к другим базам данных с помощью [ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) или драйверы OLE DB непосредственно. ODBC — это текущий интерфейс стандартной базы данных, но большинство баз данных предоставляют пользовательские функции, которые недоступны через интерфейс ODBC. OLE DB — это устаревшая технология доступа к данным COM, который по-прежнему поддерживается, но не рекомендуется для новых приложений. Дополнительные сведения см. в разделе [доступ к данным в Visual C++](/cpp/data/data-access-in-cpp).

Программы на C++, которые используют службы REST можно использовать [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Программы на C++, которые работают со службой хранилища Microsoft Azure можно использовать [клиента хранилища Microsoft Azure](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Моделирование данных&mdash;Visual Studio не поддерживает уровень ORM для C++. [ODB](https://www.codesynthesis.com/products/odb/) является популярным ORM открытым исходным кодом для C++.

Дополнительные сведения о подключении к базам данных из приложений C++, см. в разделе [Visual Studio data tools для C++](../data-tools/visual-studio-data-tools-for-cpp.md). Дополнительные сведения о технологии доступа к данным для предыдущих версий Visual C++, см. в разделе [доступ к данным](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript в Visual Studio](/scripting/javascript/javascript-language-reference) — полноправный язык для создания кроссплатформенных приложений, приложений универсальной платформы Windows, облачных служб, веб-сайтов и веб-приложений. Bower, Grunt, Gulp, npm и NuGet из среды Visual Studio можно использовать для установки свои любимые библиотеки JavaScript и базам данных. Подключение к службе хранилища Azure и служб, загрузив пакетов SDK в [веб-сайте Azure](https://azure.microsoft.com/). Edge.js — это библиотека, которая подключается к источникам данных ADO.NET JavaScript на стороне сервера (Node.js).

## <a name="python"></a>Python

Установка [поддержка Python в Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) для создания приложений Python. Документация по Azure имеет несколько учебников по подключению к данным, включая следующие:

- [Django и базы данных SQL в Azure](/azure/app-service/app-service-web-get-started-python)
- [Django и MySQL в Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Работа с [большие двоичные объекты](/azure/storage/blobs/storage-quickstart-blobs-python), [файлы](/azure/storage/files/storage-python-how-to-use-file-storage), [очереди](/azure/storage/queues/storage-python-how-to-use-queue-storage), и [таблицы (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>См. также

[Платформа искусственного Интеллекта Майкрософт](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;введение в интеллектуальное облако Microsoft, включая Cortana Analytics Suite и поддержку для Интернета вещей.

[Служба хранилища Microsoft Azure](/azure/storage/)&mdash;описываются хранилища Azure и способы создания приложений с помощью больших двоичных объектов Azure, таблиц, очередей и файлов.

[База данных SQL Azure](/azure/sql-database/)&mdash;описывается подключение к базе данных SQL Azure, реляционной базы данных как услуга.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;описаны средства, упрощающие проектирование, исследования, тестирования и развертывания приложений, подключенных к данных и баз данных.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;описание архитектуры ADO.NET и способов использования классов ADO.NET для управления данными приложения и взаимодействия с источниками данных и XML.

[Платформа ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/)&mdash;описывается создание приложений данных, которые позволяют разработчикам программировать на основе концептуальной модели, а не непосредственно к реляционной базе данных.

[Службы данных WCF 4.5](/dotnet/framework/data/wcf/index)&mdash;описывается использование [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] для развертывания служб данных в Интернете или интрасети, которые реализуют [Open Data Protocol (OData)](https://www.odata.org/).

[Данные в решениях Office](../vsto/data-in-office-solutions.md)&mdash;содержит ссылки на разделы с пояснением работы данных в решениях Office. Сюда входят сведения о схемо ориентированном программировании, кэшировании данных и доступа к данным на стороне сервера.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;описывает возможности запросов, встроенных в C# и Visual Basic и общей модели для запроса реляционных баз данных, XML документы, наборы данных и коллекциям в памяти.

[Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;рассматривается работа с возможности .NET Framework XML данные отладки XSLT, XML и архитектура XML-запрос.

[XML-документы и данные](/dotnet/standard/data/xml/index)&mdash;здесь приводится обзор подробного и интегрированного набора классов, которые работают с XML-документами и данными в .NET Framework.
