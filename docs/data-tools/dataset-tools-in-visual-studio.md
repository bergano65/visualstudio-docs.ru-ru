---
title: Средства набора данных в Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 71e660260c6ec6dfd671d4b6b2d036ffd6cffb3a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756175"
---
# <a name="dataset-tools-in-visual-studio"></a>Средства набора данных в Visual Studio
> [!NOTE]
>  Наборы данных и связанные классы являются устаревших технологий .NET из спам, позволяют приложениям работать с данными в памяти, а приложения отключаются от базы данных. Они особенно полезны для приложений, которые позволяют пользователям изменять данные и сохранять изменения в базе данных. Несмотря на то, что наборы данных оказались очень успешной технологии, рекомендуется новых приложений .NET использовать Entity Framework. Entity Framework предоставляет более естественный способ работы с табличными данными как объектные модели, и он имеет более простой интерфейс программирования.

 Объект `DataSet` объект — это объект в памяти, который по сути мини-база данных. Он содержит `DataTable`, `DataColumn`, и `DataRow` объектов, в которых можно хранить и изменять данные из одного или нескольких баз данных без необходимости открытых соединений. Набор данных хранит сведения об изменениях в данных, поэтому обновления может отследить и отправляется в базу данных, когда приложение становится повторно подключен.

 Наборы данных и родственные классы, определенные в *System.Data* пространства имен в библиотеке классов .NET Framework. Вы можете создавать и изменять наборы данных динамически в коде. Дополнительные сведения о том, как это сделать, см. в разделе ADO.NET. Документация в этом разделе показано, как работать с наборами данных с помощью конструкторов Visual Studio. Следует знать: наборы данных, которые выполняются через конструкторы использовать объектов TableAdapter для взаимодействия с базой данных. В то время как наборы данных, которые выполняются программно использовать `DataAdapter` объектов. Сведения о создании наборов данных программными средствами, см. в разделе [объекты DataAdapter и DataReader](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

 Если приложения должен только считывать данные из базы данных, а не выполнения обновлений, добавляет или удаляет, обычно можно получить более высокую производительность с помощью `DataReader` объекта для извлечения данных в универсальный `List` объекта или другой объект в коллекции. При отображении данных, можно осуществить данных привязку интерфейса пользователя в коллекцию.

## <a name="dataset-workflow"></a>Набор данных рабочего процесса
 Visual Studio предоставляет средства для упрощения работы с наборами данных. Ниже приведен базовый рабочий процесс end-to-end.

-   Используйте **источника данных** окно, чтобы создать новый набор данных из одного или нескольких источников данных. Используйте **конструктор наборов данных** для настройки набора данных и задать его свойства. Например необходимо указать, какие таблицы из источника данных для включения и какие столбцы из каждой таблицы. Тщательно выбирайте для экономии объем памяти, требующий набора данных. Дополнительные сведения см. в разделе, посвященном [созданию и настройке наборов данных](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Определяют связи между таблицами, таким образом, чтобы внешние ключи обрабатываются правильно. Дополнительные сведения см. в разделе [заполнения набора данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md).

-   Используйте **мастер настройки адаптера таблицы** для указания запроса или хранимой процедуры, которая заполняет набор данных и какие операции базы данных (update, delete и т. д.) для реализации. Дополнительные сведения см. в следующих разделах.

    -   [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)

    -   [Изменение данных в наборах данных](../data-tools/edit-data-in-datasets.md)

    -   [Проверка данных в наборах данных](../data-tools/validate-data-in-datasets.md)

    -   [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)

-   Запросы и поиск данных в наборе данных. Дополнительные сведения см. в разделе [запрашивайте наборы данных](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] позволяет [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) над данными в <xref:System.Data.DataSet> объекта. Дополнительные сведения см. в разделе [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

-   Используйте **источников данных** окно для привязки элементов управления пользовательского интерфейса для набора данных или ее отдельных столбцов, а также указать, какие столбцы являются изменяемых пользователем. Дополнительные сведения см. в разделе [привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Наборы данных и многоуровневой архитектуры
 Сведения о наборах данных в N-уровневых приложениях см. в разделе [работа с наборами данных в n уровневых приложениях](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Наборы данных и XML
 Сведения о преобразовании наборов данных в XML и обратно, см. в разделе [чтения XML-данных в набор данных](../data-tools/read-xml-data-into-a-dataset.md) и [сохранение набора данных в формате XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>См. также

- [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)