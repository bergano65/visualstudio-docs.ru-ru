---
title: Доступ к данным
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 2be1de65bb29ddca611366fcdc046162bdafc4b7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673126"
---
# <a name="accessing-data-in-visual-studio"></a>Доступ к данным в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio можно создавать приложения, которые подключаются к данным практически в любом продукте или службе базы данных, в любом формате, где угодно — на локальном компьютере, в локальной сети или в общедоступном, частном или гибридном облаке.

 Для приложений, написанных на JavaScript, Python, PHP, C++Ruby или, вы подключаетесь к данным, как и любые другие, путем получения библиотек и написания кода. Для приложений .NET Visual Studio предоставляет средства, которые можно использовать для просмотра источников данных, создания объектных моделей для хранения данных и управления ими в памяти, а также для привязки данных к пользовательскому интерфейсу.     Microsoft Azure предоставляет пакеты SDK для .NET, Java, Node. js, PHP, Python, Ruby и мобильных приложений, а также средства в Visual Studio для подключения к службе хранилища Azure.

 В следующих списках показаны лишь некоторые из многих баз данных и систем хранения, которые можно использовать из Visual Studio. Предложения [Microsoft Azure](https://azure.microsoft.com/) — это службы данных, включающие все подготовку и администрирование базового хранилища данных.  [Инструменты Azure для Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) — это дополнительный компонент, который позволяет работать с хранилищами данных Azure непосредственно из Visual Studio. Большинство других перечисленных здесь продуктов баз данных SQL и NoSQL могут размещаться на локальном компьютере, в локальной сети или в Microsoft Azure на виртуальной машине. В этом сценарии вы несете ответственность за управление самой базой данных.

 **Microsoft Azure**

||||
|-|-|-|
|База данных SQL|DocumentDB|Хранилище (большие двоичные объекты, таблицы, очереди, файлы)|
|Хранилище данных SQL|SQL Server Stretch Database|StorSimple|

 И многое другое!

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016, включая Express и LocalDB|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 И многое другое!

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|ндатабасе|ориентдб|RavenDB|
|велоЦитидб|||

 И многое другое!

 Многие поставщики баз данных и сторонние производители поддерживают интеграцию с Visual Studio с помощью пакетов NuGet. Вы можете исследовать предложения в nuget.org или с помощью диспетчера пакетов NuGet в Visual Studio (**средства**  > **диспетчер пакетов NuGet**  > **управления пакетами NuGet для решения**). Другие продукты баз данных интегрируются с Visual Studio как расширение.   Вы можете просмотреть эти предложения в коллекции Visual Studio, перейдя к **средствам**  > **расширения и обновления** , а затем выбрав пункт в **сети** в левой области диалогового окна.  Дополнительные сведения см. в разделе [Установка систем баз данных, средств и примеров](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Расширенная поддержка для SQL Server 2005 закончилась 12 апреля 2016.   Нет никакой гарантии, что средства работы с данными в Visual Studio 2015 и более поздних версий будут продолжать работать с SQL Server 2005 после этой даты. Дополнительные сведения см. в [объявлении об окончании поддержки для SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Языки .NET
 Весь доступ к данным .NET, включая в .NET Core, основан на ADO.NET, наборе классов, определяющих интерфейс для доступа к любому типу источника данных — реляционному и нереляционному. Visual Studio содержит несколько средств и конструкторов, которые работают с ADO.NET для подключения к базам данных, управления данными и предоставления данных пользователю. В документации в этом разделе описывается использование этих средств. Вы также можете программировать непосредственно для командных объектов ADO.NET. Дополнительные сведения о непосредственном вызове API-интерфейсов ADO.NET см. в разделе [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) библиотеки MSDN.

 Документацию по доступу к данным, специально связанная с ASP.NET, см. в разделе [Работа с данными](http://www.asp.net/web-forms/overview/presenting-and-managing-data) на сайте ASP.NET. Руководство по использованию Entity Framework с ASP.NET MVC см. в разделе [Начало работы с Entity Framework 6 Code First с помощью MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Приложения универсальная платформа Windows (UWP) в C# или Visual Basic могут использовать пакет Microsoft Azure SDK для .NET для доступа к службе хранилища Azure и другим службам Azure. Класс Windows. Web. HttpClient обеспечивает взаимодействие с любой службой RESTFUL. Дополнительные сведения см. в разделе [Подключение к HTTP-серверу с помощью Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Для хранения данных на локальном компьютере рекомендуемым подходом является использование SQLite, который выполняется в том же процессе, что и приложение. Если требуется уровень объектно-реляционного сопоставления (ORM), можно использовать Entity Framework. Дополнительные сведения см. в статье [доступ к данным](https://msdn.microsoft.com/windows/uwp/data-access/index) в центре разработчиков Windows.

 При подключении к службам Azure обязательно Скачайте последние версии [средств Azure SDK](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Поставщики данных
 Чтобы базу данных можно было использовать в ADO.NET, она должна иметь настраиваемый *поставщик данных ADO.NET* или интерфейс ODBC или OLE DB. Корпорация Майкрософт предоставляет [список поставщиков данных ADO.NET](https://msdn.microsoft.com/data/dd363565) для SQL Server продуктов, а также поставщиков ODBC и OLE DB.

#### <a name="data-modeling"></a>Моделирование данных
 В .NET существует три варианта моделирования и манипулирования данными в памяти после их извлечения из источника данных.

 Entity Framework предпочтительную технологию Microsoft ORM. Его можно использовать для программирования реляционных данных в качестве объектов .NET первого класса. Для новых приложений он должен быть первым выбором по умолчанию, если требуется модель. Для этого требуется пользовательская поддержка от базового поставщика ADO.NET.

 LINQ to SQL объектно-реляционный модуль сопоставления более раннего поколения. Он хорошо работает для менее сложных сценариев, но больше не находится в активной разработке.

 Набор данных — это самая старая из трех технологий моделирования. Она разработана в основном для быстрой разработки приложений "формы по данным", в которых не выполняется обработка огромных объемов данных или выполнение сложных запросов или преобразований. Объект DataSet состоит из объектов DataTable и DataRow, которые логически похожи на объекты базы данных SQL гораздо больше, чем объекты .NET. Для относительно простых приложений, основанных на источниках данных SQL, все еще могут быть хорошим выбором.

 Использование этих технологий не требуется. В некоторых сценариях, особенно если важна производительность, можно просто использовать объект DataReader для чтения из базы данных и копирования нужных значений в объект коллекции, такой как List \<T >.

### <a name="native-c"></a>Неуправляемый C++
 C++приложения, подключающиеся к SQL Server, должны использовать [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Доступ к другим базам данных можно получить с помощью [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) или драйверов OLE DB напрямую. ODBC — это текущий стандартный интерфейс базы данных, но большинство систем баз данных предоставляют настраиваемые функции, доступ к которым через интерфейс ODBC невозможен.  OLE DB — это устаревшая технология доступа к данным COM, которая по-прежнему поддерживается, но не рекомендуется для новых приложений.  Дополнительные сведения см. в разделе [доступ к данным](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 C++программы, использующие службы RESTful, могут использовать [ C++ пакет SDK для оставшейся](https://github.com/Microsoft/cpprestsdk)работы.

 C++программы, работающие с служба хранилища Microsoft Azure, могут использовать [клиент служба хранилища Microsoft Azure](http://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Моделирование данных
 Visual Studio не предоставляет уровень ORM для C++.  [ODB](http://www.codesynthesis.com/products/odb/) — это популярная модель ORM с открытым C++кодом для.

 Дополнительные сведения о стандартных технологиях C++ доступа к данным см. в разделе [доступ к данным](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b) .

### <a name="javascript"></a>JavaScript
 [JavaScript в Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) — это язык первого класса для создания кросс-платформенных приложений, приложений UWP, облачных служб, веб-сайтов и веб-приложений. Вы можете использовать Bower, grunt, gulp, NPM и NuGet в Visual Studio для установки избранных библиотек JavaScript и продуктов баз данных. Подключитесь к службе хранилища Azure и службам, загрузив пакеты SDK с [веб-сайта Azure](https://azure.microsoft.com/).  Ребр. js — это библиотека, которая соединяет серверный сценарий JavaScript (Node. js) с ADO.NET источниками данных.

### <a name="python"></a>Python
 Установите [Инструменты Python для Visual Studio](http://microsoft.github.io/PTVS/) вместе с предпочтительной платформой Python для создания приложений CPython или IronPython (.NET).  На веб-сайте Инструменты Python для Visual Studio есть несколько руководств по подключению к данным, включая [Django и базу данных SQL в Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django и MySQL в Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) , а также на [MongoDB в Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>В данном разделе
 [Установка систем баз данных, средств и примеров](../data-tools/installing-database-systems-tools-and-samples.md) Описывает, как получить продукты базы данных и расширения или драйверы Visual Studio, которые их поддерживают, а также где можно найти образцы баз данных для экспериментов и обучения.

 [Visual Studio Data Tools для .NET](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Описывает использование окон инструментов Visual Studio для подключения к источникам данных, создания или Entity Framework моделей, а также привязки данных к элементам управления пользовательского интерфейса.

## <a name="related-topics"></a>См. также
 [Данные, устройства и аналитика](https://msdn.microsoft.com/data-and-devices) Содержит введение в интеллектуальное облако Майкрософт, включая Кортану Analytics Suite и поддержку "Интернет вещей".

 [Служба хранилища Microsoft Azure](/azure/storage/) Описание службы хранилища Azure и создания приложений с помощью больших двоичных объектов, таблиц, очередей и файлов Azure.

 [База данных SQL Azure](https://azure.microsoft.com/documentation/services/sql-database/) Описывает, как подключиться к базе данных SQL Azure — реляционной базе данных в качестве службы.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Содержит описание средств, упрощающих проектирование, изучение, тестирование и развертывание приложений и баз данных, подключенных к данным.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) Описывает архитектуру ADO.NET и использование классов ADO.NET для управления данными приложения и взаимодействия с источниками данных и XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) Описывает создание приложений для работы с данными, которые позволяют разработчикам программировать на основе концептуальной модели, а не непосредственно в реляционной базе данных.

 [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Описывает использование [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] для развертывания служб данных в Интернете или интрасети, которые реализуют [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).

 [Данные в решениях Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Содержит ссылки на разделы, в которых объясняется, как работают данные в решениях Office. Сюда входят сведения о программировании на основе схемы, кэшировании данных и доступе к данным на стороне сервера.

 [LINQ (интегрированный в язык запрос)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Описывает возможности запросов, встроенные C# в и Visual Basic, а также общую модель для запросов к реляционным базам данных, XML-документам, наборам данных и коллекциям в памяти.

 [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) Описывает работу с XML-данными, отладку XSLT, .NET Framework функции XML и архитектуру XML-запросов.

 [XML-документы и данные](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Содержит обзор комплексного интегрированного набора классов, который работает с XML-документами и данными в .NET Framework.
