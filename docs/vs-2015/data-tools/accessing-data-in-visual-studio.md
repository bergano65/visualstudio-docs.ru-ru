---
title: Доступ к данным в Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 452e7dbc1f151bc39791e04d708eaf1cf870b4cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561613"
---
# <a name="accessing-data-in-visual-studio"></a>Доступ к данным в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [доступ к данным в Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio).  
  
  
В Visual Studio можно создавать приложения, которые подключаются к данным в практически любого продукта базы данных или службы, в любом формате, в любом месте — на локальном компьютере, на локальной сети или в общедоступные, частные и гибридные облака.  
  
 Для приложений на JavaScript, Python, PHP, Ruby или C++ можно подключаться к данным, как это сделать что-нибудь еще, получение библиотеки и написания кода. Для приложений .NET Visual Studio предоставляет средства, которые можно использовать для исследования источники данных и создавать модели объектов для хранения и обработки данных в памяти и привязка данных к пользовательскому интерфейсу.     Microsoft Azure предоставляет пакеты SDK для .NET, Java, Node.js, PHP, Python, Ruby и мобильных приложений и средств в Visual Studio для подключения к службе хранилища Azure.  
  
 В следующих списках приведены лишь некоторые из многих системах базы данных и хранилища, которые могут быть использованы из Visual Studio. [Microsoft Azure](https://azure.microsoft.com/en-us/) предложения — это службы данных, которые включают все подготовки и администрирования из базового хранилища данных.  [Средства Azure для Visual Studio](https://www.visualstudio.com/en-us/features/azure-tools-vs.aspx) — это необязательный компонент, который позволяет работать с хранилищами данных Azure непосредственно из Visual Studio. Большинство других SQL и NoSQL базы данных продуктов, которые перечислены здесь может размещаться на локальном компьютере, в локальной сети, а также в Microsoft Azure на виртуальной машине. В этом сценарии вы несете ответственность за управление самой базы данных.  
  
 **Microsoft Azure**  
  
||||  
|-|-|-|  
|База данных SQL|DocumentDB|Хранилища (большие двоичные объекты, таблицы, очереди, файлы)|  
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
|Данных|OrientDB|RavenDB|  
|VelocityDB|||  
  
 И многое другое!  
  
 Многими поставщиками базы данных и третьим сторонам поддерживается интеграция с Visual Studio, пакеты NuGet. Вы можете изучить предложения на сайте nuget.org или через диспетчер пакетов NuGet в Visual Studio (**средства** > **диспетчер пакетов NuGet** > **управление пакетами NuGet Пакетами для решения**). Другие продукты баз данных интеграции с Visual Studio в качестве расширения.   Эти предложения в коллекции Visual Studio можно просмотреть, перейдя по адресу **средства** > **расширения и обновления** и выбрав **Online** слева Панель диалогового окна.  Дополнительные сведения см. в разделе [установка систем баз данных, средства и примеры](../data-tools/installing-database-systems-tools-and-samples.md).  
  
> [!NOTE]
>  Расширенная поддержка SQL Server 2005 закончилась 12 апреля 2016 г.   Нет никакой гарантии, что данные средства в Visual Studio 2015 и более поздних версий будет продолжать работать с SQL Server 2005, после этой даты. Дополнительные сведения см. в разделе [end-of-support объявление о выпуске для SQL Server 2005](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/).  
  
### <a name="net-languages"></a>Языки .NET  
 Все .NET доступ к данным, включая в .NET Core основан на ADO.NET, набор классов, определяющий интерфейс для доступа к любой тип источника данных, реляционных и нереляционных. Visual Studio предоставляет несколько средств и конструкторов, которые работают с ADO.NET для подключения к базам данных, обработки данных и представления данных пользователю. Документация в этом разделе описывается, как использовать эти средства. Также можно запрограммировать напрямую с объектами команды ADO.NET. Дополнительные сведения о прямого вызова API-интерфейсы ADO.NET, см. в разделе [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) в библиотеке MSDN.  
  
 Для доступа к данным документации, относящихся к ASP.NET, см. в разделе [работа с данными](http://www.asp.net/web-forms/overview/presenting-and-managing-data) на веб-сайте ASP.NET. Учебник по использованию Entity Framework с ASP.NET MVC, см. в разделе [Приступая к работе с Entity Framework 6 Code First с помощью MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).  
  
 Универсальные приложения платформы Windows (UWP) в C# или Visual Basic можно использовать Microsoft Azure SDK для .NET для доступа к службе хранилища Azure и других служб Azure. Класс Windows.Web.HttpClient обеспечивает взаимодействие с любой службы RESTful. Дополнительные сведения см. в разделе [способ подключения к серверу HTTP, с помощью Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx.)  
  
 Для хранения данных на локальном компьютере рекомендуется использовать SQLite, которая выполняется в том же процессе, что и приложение. Если к слою объектно реляционного сопоставления (ORM) требуется, можно использовать Entity Framework. Дополнительные сведения см. в разделе [доступ к данным](https://msdn.microsoft.com/windows/uwp/data-access/index) в центре разработчиков Windows.  
  
 При подключении к службам Azure, необходимо загрузить последнюю версию [инструментов пакета Azure SDK](https://azure.microsoft.com/en-us/downloads/).  
  
#### <a name="data-providers"></a>Поставщики данных  
 Для базы данных должно использоваться в ADO.NET, он должен иметь пользовательский *поставщика данных ADO.NET* или else должны предоставлять интерфейс ODBC или OLE DB. Корпорация Майкрософт предоставляет [список поставщиков данных ADO.NET](https://msdn.microsoft.com/data/dd363565) продуктов SQL Server, а также поставщиков ODBC и OLE DB.  
  
#### <a name="data-modeling"></a>Моделирование данных  
 В .NET у вас есть три варианта для моделирования и работы с данными в памяти после ее получения из источника данных:  
  
 Entity Framework  
 Предпочтительной технологией Microsoft ORM. Его можно использовать для программирования реляционных данных как объекты .NET первичного класса. Для новых приложений это должен быть первый вариант по умолчанию, при необходимости модель. Он требует настраиваемую поддержку от базового поставщика ADO.NET.  
  
 LINQ to SQL  
 Предыдущих поколений объектно реляционного сопоставления. Он хорошо подходит для более сложных сценариев, но больше не находится в активной разработке.  
  
 Наборы данных  
 Самый старый из трех технологий моделирования. Она предназначена в первую очередь для быстрой разработки приложений «формы поверх данных», в которых не обработки огромные объемы данных или выполнения сложных запросов или преобразования. Объект DataSet состоит из объектов DataTable и DataRow, логически похожих объектов базы данных SQL гораздо больше, чем объекты .NET. Для относительно простых приложений, основанных на источниках данных SQL наборов данных может быть хорошим выбором.  
  
 Нет никаких требований к использованию в любой из этих технологий. В некоторых сценариях, особенно в том случае, если важна производительность, можно просто использовать объект DataReader для чтения из базы данных и скопируйте необходимые значения в объект коллекции, такой как список\<T >.  
  
### <a name="native-c"></a>Неуправляемый C++  
 Приложения C++, которые подключаются к SQL Server, должны использовать [собственный клиент SQL Server](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Доступ к другим базам данных с помощью [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) или драйверы OLE DB непосредственно. ODBC — это текущий интерфейс стандартной базы данных, но большинство баз данных предоставляют пользовательские функции, которые недоступны через интерфейс ODBC.  OLE DB — это устаревшая технология доступа к данным COM, который по-прежнему поддерживается, но не рекомендуется для новых приложений.  Дополнительные сведения см. в разделе [доступ к данным](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).  
  
 Программы на C++, которые используют службы REST можно использовать [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).  
  
 Программы на C++, которые работают со службой хранилища Microsoft Azure можно использовать [клиента хранилища Microsoft Azure](http://www.nuget.org/packages/wastorage).  
  
#### <a name="data-modeling"></a>Моделирование данных  
 Visual Studio не поддерживает уровень ORM для C++.  [ODB](http://www.codesynthesis.com/products/odb/) является популярным ORM открытым исходным кодом для C++.  
  
 Дополнительные сведения о технологии доступа к данным для предыдущих версий Visual C++, см. в разделе [доступа к данным](http://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)  
  
### <a name="javascript"></a>JavaScript  
 [JavaScript в Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) — полноправный язык для создания кроссплатформенных приложений, приложений универсальной платформы Windows, облачных служб, веб-сайтов и веб-приложений. Bower, Grunt, Gulp, npm и NuGet из среды Visual Studio можно использовать для установки свои любимые библиотеки JavaScript и базам данных. Подключение к службе хранилища Azure и служб, загрузив пакетов SDK в [веб-сайте Azure](https://azure.microsoft.com/).  Edge.js — это библиотека, которая подключается к источникам данных ADO.NET JavaScript на стороне сервера (Node.js).  
  
### <a name="python"></a>Python  
 Установка [инструменты Python для Visual Studio](http://microsoft.github.io/PTVS/) вместе с вашей избранные платформы Python, чтобы создавать приложения CPython и IronPython (.NET).  Инструменты Python для Visual Studio веб-сайта есть несколько учебников по подключению к данным, включая [Django и базы данных SQL в Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django и MySQL в Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) и [Bottle и MongoDB в Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Установка систем баз данных, средств и примеров](../data-tools/installing-database-systems-tools-and-samples.md)  
 Описывается, как получить продукты баз данных и расширения Visual Studio или драйверы, которые их поддерживают и где найти образцы баз данных для службы "Экспериментирование" и в целях обучения.  
  
 [Visual Studio Data Tools для .NET](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)  
 В этой статье описывается использование окон инструментов Visual Studio для подключения к источникам данных, создать наборы данных или модели Entity Framework и привязки данных к элементам пользовательского интерфейса.  
  
## <a name="related-topics"></a>См. также  
 [Данные, устройства и аналитика](https://msdn.microsoft.com/data-and-devices)  
 Введение в интеллектуальное облако Microsoft, включая Cortana Analytics Suite и поддержку для Интернета вещей.  
  
 [Хранилище Microsoft Azure](https://azure.microCsoft.com/en-us/documentation/services/storage/)  
 Описание службы хранилища Azure и способы создания приложений с помощью больших двоичных объектов Azure, таблиц, очередей и файлов.  
  
 [База данных SQL Azure](https://azure.microsoft.com/en-us/documentation/services/sql-database/)  
 В этой статье описывается подключение к базе данных SQL Azure, реляционной базы данных как услуга.  
  
 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)  
 Описывает средства, упрощающие проектирование, исследования, тестирования и развертывания приложений, подключенных к данных и баз данных.  
  
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)  
 Описывает архитектуру ADO.NET и способы использования классов ADO.NET для управления данными приложения и взаимодействия с источниками данных и XML.  
  
 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)  
 В этой статье описывается создание приложений данных, которые позволяют разработчикам программировать на основе концептуальной модели, а не непосредственно к реляционной базе данных.  
  
 [Службы данных WCF 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a)  
 Описывает использование [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] для развертывания служб данных в Интернете или интрасети, которые реализуют [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204).  
  
 [Данные в решениях Office](http://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a)  
 Содержит ссылки на разделы с пояснением работы данных в решениях Office. Сюда входят сведения о схемо ориентированном программировании, кэшировании данных и доступа к данным на стороне сервера.  
  
 [Встроенный язык запросов LINQ](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 Описывает возможности запросов, встроенных в C# и Visual Basic и общей модели для запроса реляционных баз данных, XML документы, наборы данных и коллекциям в памяти.  
  
 [Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)  
 Описывается работа с XML, отладки XSLT, .NET Framework XML признаков и архитектура XML-запрос.  
  
 [XML-документы и данные](http://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380)  
 Здесь приводится обзор обширного и встроенного набора классов, предназначенных для работы с XML-документами и данными в .NET Framework.

