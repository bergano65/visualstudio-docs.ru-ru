---
title: "Средства набора данных в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.data.DataSet
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
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 6a7e5741b11263ef3c3730ddaa69e566cd7c2e24
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="dataset-tools-in-visual-studio"></a>Средства набора данных в Visual Studio
> [!NOTE]
>  Наборы данных и связанных классов — устаревший технологии .NET из спам, позволяют приложениям работать с данными в памяти, пока приложения отключаются от базы данных. Они особенно полезны для приложений, которые позволяют пользователям изменять данные и сохранять изменения в базе данных. Несмотря на то, что наборы данных доказали очень успешной технологии, рекомендуется новых приложений .NET использовать Entity Framework. Entity Framework предоставляет более естественным способом работы с табличными данными как объект модели, и он имеет более простой интерфейс программирования.  
  
 Объект набора данных представляет объект в памяти, по существу мини-базы данных. В нем объектов DataTable и DataColumn, DataRow, в которых можно хранить и изменять данные из одного или нескольких баз данных без необходимости открытых соединений. Набор данных хранит сведения об изменениях в его данных, поэтому обновлений может отследить и отправляются в базу данных при подключении приложения становится.  
  
 Наборы данных и связанные с ним классы определяются в пространстве имен System.Data в библиотеке классов .NET Framework. Можно создавать и изменять наборы данных динамически в коде. Дополнительные сведения о том, как это сделать, см. в разделе ADO.NET. Документация в этом разделе показано, как для работы с наборами данных с помощью конструкторов Visual Studio. Также необходимо знать: наборы данных, которые выполняются через конструкторы объектов TableAdapter использовать для взаимодействия с базой данных, тогда как наборы данных, которые выполняются программно использовать объекты DataAdapter. Сведения о создании наборов данных программным путем см. в разделе [DataAdapter и DataReader](/dotnet/framework/data/adonet/dataadapters-and-datareaders).  
  
 Если нужно только считывать данные из базы данных и не выполнять обновления, добавляет или удаляет приложения, обычно можно получить более высокую производительность с помощью объекта DataReader для получения данных в объект универсального списка или другой объект в коллекции. При отображении данных, то можно связывать пользовательского интерфейса в коллекцию.  
  
## <a name="dataset-workflow"></a>Набор данных рабочего процесса  
 Visual Studio предоставляет множество средств для упрощения работы с наборами данных. — Базовый рабочий процесс конца в конец:  
  
-   Используйте **источника данных** окно для создания нового набора данных из одного или нескольких источников данных. Используйте **конструктора наборов данных** для настройки набора данных и задать его свойства. Например необходимо указать, какие таблицы из источника данных для включения и какие столбцы из каждой таблицы. Тщательно выбирайте для экономии объем памяти, который требуется набор данных. Дополнительные сведения см. в разделе, посвященном [созданию и настройке наборов данных](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Укажите связи между таблицами, внешние ключи обрабатываются правильно. Дополнительные сведения см. в разделе [заполнения набора данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
-   Используйте **мастер настройки адаптера таблицы** для указания запроса или хранимой процедуры, которая заполняет набор данных и какие операции базы данных (update, delete и т. д.) для реализации. Дополнительные сведения см. в следующих разделах.  
  
    -   [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [Изменение данных в наборах данных](../data-tools/edit-data-in-datasets.md)  
  
    -   [Проверка данных в наборах данных](../data-tools/validate-data-in-datasets.md)  
  
    -   [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)  
  
-   Запрос и поиск данных в наборе данных. Дополнительные сведения см. в разделе [запросов наборов данных](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)]включает [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d) над данными в <xref:System.Data.DataSet> объекта. Дополнительные сведения см. в разделе [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
-   Используйте **источники данных** окна для привязки элементов управления пользовательского интерфейса для набора данных или его отдельных столбцов, а также указать, какие столбцы являются изменяемые пользователем. Дополнительные сведения см. в разделе [привязки элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="datasets-and-n-tier-architecture"></a>Наборы данных и N-уровневые архитектуры  
 Сведения о наборах данных в N-уровневых приложениях см. в разделе [работы с наборами данных в n уровневых приложениях](../data-tools/work-with-datasets-in-n-tier-applications.md).  
  
## <a name="datasets-and-xml"></a>Наборы данных и XML  
 Сведения о преобразовании наборов данных в XML и обратно в разделе [чтения XML-данных в набор данных](../data-tools/read-xml-data-into-a-dataset.md) и [сохранить набор данных в формате XML](../data-tools/save-a-dataset-as-xml.md).  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)