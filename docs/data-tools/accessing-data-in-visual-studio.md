---
title: Работа с данными в Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7c7aa1544f998a88424c0087fadceab63757d23b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "77272091"
---
# <a name="work-with-data-in-visual-studio"></a>Работа с данными в Visual Studio

В Visual Studio можно создавать приложения, которые подключаются к данным практически в любом продукте или службе базы данных, в любом формате, где угодно — на локальном компьютере, в локальной сети или в общедоступном, частном или гибридном облаке.

Для приложений на JavaScript, Python, PHP, Ruby или C++ вы подключаетесь к данным, как и любые другие, путем получения библиотек и написания кода. Для приложений .NET Visual Studio предоставляет средства, которые можно использовать для просмотра источников данных, создания объектных моделей для хранения данных и управления ими в памяти, а также для привязки данных к пользовательскому интерфейсу. Microsoft Azure предоставляет пакеты SDK для .NET, Java, Node.js, PHP, Python, Ruby и мобильных приложений, а также средства в Visual Studio для подключения к службе хранилища Azure.

::: moniker range="vs-2017"
В следующих списках показаны лишь некоторые из многих баз данных и систем хранения, которые можно использовать из Visual Studio. Предложения [Microsoft Azure](https://azure.microsoft.com/) — это службы данных, включающие все подготовку и администрирование базового хранилища данных. Рабочая нагрузка **разработки Azure** в [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) позволяет работать с хранилищами данных Azure непосредственно из Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
В следующих списках показаны лишь некоторые из многих баз данных и систем хранения, которые можно использовать из Visual Studio. Предложения [Microsoft Azure](https://azure.microsoft.com/) — это службы данных, включающие все подготовку и администрирование базового хранилища данных. Рабочая нагрузка **разработки Azure** в [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) позволяет работать с хранилищами данных Azure непосредственно из Visual Studio.
::: moniker-end

![Рабочая нагрузка "Разработка для Azure".](media/azure-development-workload.png)

Большинство других перечисленных здесь продуктов баз данных SQL и NoSQL могут размещаться на локальном компьютере, в локальной сети или в Microsoft Azure на виртуальной машине. Если база данных размещена на Microsoft Azure виртуальной машине, вы несете ответственность за управление самой базой данных.

**Microsoft Azure**

- База данных SQL
- Azure Cosmos DB
- Хранилище (большие двоичные объекты, таблицы, очереди, файлы)
- Хранилище данных SQL
- SQL Server Stretch Database
- StorSimple
- И многое другое.

**SQL**

- SQL Server 2005-2016 (включает Express и LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle;
- PostgreSQL
- SQLite
- И многое другое.

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- ндатабасе
- Ориентдб |
- RavenDB
- велоЦитидб
- И многое другое.

::: moniker range="vs-2017"

Многие поставщики баз данных и сторонние производители поддерживают интеграцию с Visual Studio с помощью пакетов NuGet. Вы можете исследовать предложения в NuGet.org или с помощью диспетчера пакетов NuGet в Visual Studio (**инструменты**  >  **Диспетчер пакетов NuGet**  >  **Управление пакетами NuGet для решения**). Другие продукты баз данных интегрируются с Visual Studio как расширение. Эти предложения можно просмотреть в [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или перейдя к **средствам**  >  **расширения и обновления** , а затем выбрав пункт в **сети** в левой области диалогового окна. Дополнительные сведения см. в разделе [совместимые системы баз данных для Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Многие поставщики баз данных и сторонние производители поддерживают интеграцию с Visual Studio с помощью пакетов NuGet. Вы можете исследовать предложения в NuGet.org или с помощью диспетчера пакетов NuGet в Visual Studio (**инструменты**  >  **Диспетчер пакетов NuGet**  >  **Управление пакетами NuGet для решения**). Другие продукты баз данных интегрируются с Visual Studio как расширение. Эти предложения можно просмотреть в [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или перейдя к **расширениям**  >  **Управление расширениями** , а затем выбрав "в **сети** " в левой области диалогового окна. Дополнительные сведения см. в разделе [совместимые системы баз данных для Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Расширенная поддержка SQL Server 2005 закончилась 12 апреля 2016 г. Нет никакой гарантии, что средства работы с данными в Visual Studio 2015 и более поздних версий будут продолжать работать с SQL Server 2005. Дополнительные сведения см. в [объявлении об окончании поддержки для SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Языки платформы .NET

Весь доступ к данным .NET, включая в .NET Core, основан на ADO.NET, наборе классов, определяющих интерфейс для доступа к любому типу источника данных — реляционному и нереляционному. Visual Studio содержит несколько средств и конструкторов, которые работают с ADO.NET для подключения к базам данных, управления данными и предоставления данных пользователю. В документации в этом разделе описывается использование этих средств. Вы также можете программировать непосредственно для командных объектов ADO.NET. Дополнительные сведения о непосредственном вызове API-интерфейсов ADO.NET см. в разделе [ADO.NET](/dotnet/framework/data/adonet/index).

Документацию по доступу к данным, связанную с ASP.NET, см. в разделе [Работа с данными](https://www.asp.net/web-forms/overview/presenting-and-managing-data) на сайте ASP.NET. Руководство по использованию Entity Framework с ASP.NET MVC см. в разделе [Начало работы с Entity Framework 6 Code First с помощью MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Приложения универсальная платформа Windows (UWP) на C# или Visual Basic могут использовать Пакет Microsoft Azure SDK для .NET для доступа к службе хранилища Azure и другим службам Azure. Класс Windows. Web. HttpClient обеспечивает взаимодействие с любой службой RESTFUL. Дополнительные сведения см. в разделе [Подключение к HTTP-серверу с помощью Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Для хранения данных на локальном компьютере рекомендуемым подходом является использование SQLite, который выполняется в том же процессе, что и приложение. Если требуется уровень объектно-реляционного сопоставления (ORM), можно использовать Entity Framework. Дополнительные сведения см. в статье [доступ к данным](/windows/uwp/data-access/index) в центре разработчиков Windows.

При подключении к службам Azure обязательно Скачайте последние версии [средств Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Поставщики данных

Чтобы базу данных можно было использовать в ADO.NET, она должна иметь настраиваемый *поставщик данных ADO.NET* или интерфейс ODBC или OLE DB. Корпорация Майкрософт предоставляет [список поставщиков данных ADO.NET](/dotnet/framework/data/adonet/ado-net-overview) для продуктов SQL Server, а также поставщиков ODBC и OLE DB.

### <a name="data-modeling"></a>Моделирование данных

В .NET существует три варианта моделирования и манипулирования данными в памяти после их извлечения из источника данных.

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Предпочтительная технология Microsoft ORM. Его можно использовать для программирования реляционных данных в качестве объектов .NET первого класса. Для новых приложений он должен быть первым выбором по умолчанию, если требуется модель. Для этого требуется пользовательская поддержка от базового поставщика ADO.NET.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Объектно-реляционное средство сопоставления более раннего поколения. Он хорошо работает для менее сложных сценариев, но больше не находится в активной разработке.

[Наборы данных](../data-tools/dataset-tools-in-visual-studio.md) Самая старая из трех технологий моделирования. Она разработана в основном для быстрой разработки приложений "формы по данным", в которых не выполняется обработка огромных объемов данных или выполнение сложных запросов или преобразований. Объект DataSet состоит из объектов DataTable и DataRow, которые логически похожи на объекты базы данных SQL гораздо больше, чем объекты .NET. Для относительно простых приложений, основанных на источниках данных SQL, все еще могут быть хорошим выбором.

Использование этих технологий не требуется. В некоторых сценариях, особенно если важна производительность, можно просто использовать объект DataReader для чтения из базы данных и копирования нужных значений в объект коллекции, например в List \<T> .

## <a name="native-c"></a>Машинный C++

Приложения C++, подключающиеся к SQL Server, должны использовать [драйвер Microsoft® ODBC 13,1 для SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) в большинстве случаев. Если серверы связаны, OLE DB является обязательным и для использования [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Доступ к другим базам данных можно получить с помощью [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) или драйверов OLE DB напрямую. ODBC — это текущий стандартный интерфейс базы данных, но большинство систем баз данных предоставляют настраиваемые функции, доступ к которым через интерфейс ODBC невозможен. OLE DB — это устаревшая технология доступа к данным COM, которая по-прежнему поддерживается, но не рекомендуется для новых приложений. Дополнительные сведения см. [в разделе доступ к данным в Visual C++](/cpp/data/data-access-in-cpp).

Программы на языке c++, использующие службы RESTFUL, могут использовать [пакет SDK для c++ для других](https://github.com/Microsoft/cpprestsdk)приложений.

Программы на языке C++, работающие с служба хранилища Microsoft Azure, могут использовать [клиент служба хранилища Microsoft Azure](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Моделирование данных &mdash; Visual Studio не предоставляет уровень ORM для C++. [ODB](https://www.codesynthesis.com/products/odb/) — это популярная модель ORM с открытым кодом для C++.

Дополнительные сведения о подключении к базам данных из приложений C++ см. в статье [Visual Studio Data Tools for c++](../data-tools/visual-studio-data-tools-for-cpp.md). Дополнительные сведения об устаревших Visual C++ технологиях доступа к данным см. в разделе [доступ к данным](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript в Visual Studio](/scripting/javascript/javascript-language-reference) — это язык первого класса для создания кросс-платформенных приложений, приложений UWP, облачных служб, веб-сайтов и веб-приложений. Вы можете использовать Bower, grunt, gulp, NPM и NuGet в Visual Studio для установки избранных библиотек JavaScript и продуктов баз данных. Подключитесь к службе хранилища Azure и службам, загрузив пакеты SDK с [веб-сайта Azure](https://azure.microsoft.com/). Edge.js — это библиотека, которая подключает серверный код JavaScript (Node.js) к источникам данных ADO.NET.

## <a name="python"></a>Python

Установите [поддержку Python в Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) для создания приложений Python. В документации по Azure есть несколько руководств по подключению к данным, включая следующие:

- [Django и база данных SQL в Azure](/azure/app-service/app-service-web-get-started-python)
- [Django и MySQL в Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Работа с [большими двоичными объектами](/azure/storage/blobs/storage-quickstart-blobs-python), [файлами](/azure/storage/files/storage-python-how-to-use-file-storage), [очередями](/azure/storage/queues/storage-python-how-to-use-queue-storage)и [таблицами (Космо DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Связанные темы

Платформа искусственного [интеллекта Майкрософт](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Содержит введение в интеллектуальное облако Майкрософт, включая Кортану Analytics Suite и поддержку "Интернет вещей".

[Служба хранилища Microsoft Azure](/azure/storage/) &mdash; Описание службы хранилища Azure и создания приложений с помощью больших двоичных объектов, таблиц, очередей и файлов Azure.

[База данных](/azure/sql-database/) &mdash; SQL Azure Описывает, как подключиться к базе данных SQL Azure — реляционной базе данных в качестве службы.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Содержит описание средств, упрощающих проектирование, изучение, тестирование и развертывание приложений и баз данных, подключенных к данным.

[ADO.NET](/dotnet/framework/data/adonet/index) &mdash; Описывает архитектуру ADO.NET и использование классов ADO.NET для управления данными приложения и взаимодействия с источниками данных и XML.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; Описывает создание приложений для работы с данными, которые позволяют разработчикам программировать на основе концептуальной модели, а не непосредственно в реляционной базе данных.

[WCF Data Services 4,5](/dotnet/framework/data/wcf/index) &mdash; Описывает использование [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] для развертывания служб данных в Интернете или интрасети, которые реализуют [Open Data Protocol (OData)](https://www.odata.org/).

[Данные в решениях Office](../vsto/data-in-office-solutions.md) &mdash; Содержит ссылки на разделы, в которых объясняется, как работают данные в решениях Office. Сюда входят сведения о программировании на основе схемы, кэшировании данных и доступе к данным на стороне сервера.

[LINQ (интегрированный в язык запрос)](/dotnet/csharp/linq/) &mdash; Описывает возможности запросов, встроенные в C# и Visual Basic, а также общую модель для запросов к реляционным базам данных, XML-документам, наборам данных и коллекциям в памяти.

[Средства XML в Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; Описывает работу с XML-данными, отладку XSLT, функции XML .NET и архитектуру XML-запросов.

[XML-документы и данные](/dotnet/standard/data/xml/index) &mdash; Содержит общие сведения о комплексном и интегрированном наборе классов, работающих с XML-документами и данными в .NET.
