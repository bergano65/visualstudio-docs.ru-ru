---
title: Средства набора данных
description: Ознакомьтесь с инструментами набора данных, доступными в Visual Studio. Прочтите сведения о рабочем процессе, наборах данных и N-уровневой архитектуре, наборах DataSet и XML.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4e711d60010117f3a5081470ab8e6e656a7e6e90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867000"
---
# <a name="dataset-tools-in-visual-studio"></a>Инструменты для работы с наборами данных в Visual Studio

> [!NOTE]
> Наборы данных и связанные классы — это устаревшие технологии .NET от ранних версий 2000, которые позволяют приложениям работать с данными в памяти, когда приложения отключаются от базы данных. Они особенно полезны для приложений, которые позволяют пользователям изменять данные и сохранять изменения обратно в базу данных. Несмотря на то что наборы данных признаны очень успешными, рекомендуется использовать в новых приложениях .NET Entity Framework. Entity Framework предоставляет более естественный способ работы с табличными данными в качестве объектных моделей и имеет более простой интерфейс программирования.

`DataSet`Объект — это объект в памяти, который, по сути, является мини-базой данных. Он содержит `DataTable` `DataColumn` объекты, и, `DataRow` в которых можно хранить и изменять данные из одной или нескольких баз данных без необходимости поддерживать открытое соединение. Набор данных хранит сведения об изменениях в данных, поэтому обновления могут быть отосланы и отправлены обратно в базу данных при повторном подключении приложения.

Наборы данных и связанные классы определяются в <xref:System.Data?displayProperty=fullName> пространстве имен в API .NET. Вы можете создавать и изменять наборы данных динамически в коде с помощью ADO.NET. В документации в этом разделе показано, как работать с наборами данных с помощью Visual Studio Designers. Наборы данных, созданные с помощью конструкторов, используют объекты **TableAdapter** для взаимодействия с базой. Наборы данных, которые создаются программно, используют объекты **DataAdapter** . Дополнительные сведения о создании наборов данных программным путем см. в разделе [адаптеры данных и DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Если приложению требуется только считывать данные из базы данных, а не выполнять обновления, добавлять или удалять, обычно можно получить лучшую производительность, используя `DataReader` объект для получения данных в универсальный `List` объект или другой объект коллекции. При отображении данных можно связать пользовательский интерфейс с коллекцией данных.

## <a name="dataset-workflow"></a>Рабочий процесс набора данных

Visual Studio предоставляет инструментарий для упрощения работы с наборами данных. Базовый сквозной рабочий процесс:

- Используйте [окно Источники данных](add-new-data-sources.md#data-sources-window) для создания нового набора данных из одного или нескольких источников данных. Используйте **Конструктор наборов данных** , чтобы настроить набор данных и задать его свойства. Например, необходимо указать, какие таблицы из источника данных следует включить, и какие столбцы из каждой таблицы. Тщательно выбирайте, чтобы сэкономить объем памяти, требуемый для набора данных. Дополнительные сведения см. в разделе, посвященном [созданию и настройке наборов данных](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Укажите связи между таблицами, чтобы внешние ключи обрабатывались правильно. Дополнительные сведения см. в разделе [Заполнение наборов данных с помощью адаптеров таблиц](../data-tools/fill-datasets-by-using-tableadapters.md).

- Используйте **Мастер настройки TableAdapter** , чтобы указать запрос или хранимую процедуру, заполняющую набор данных, и какие операции с базой данных (обновление, удаление и т. д.) следует реализовать. Дополнительные сведения см. в следующих статьях:

  - [Заполнение наборов данных с помощью адаптеров таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Изменение данных в наборах данных](../data-tools/edit-data-in-datasets.md)

  - [Проверка данных в наборах данных](../data-tools/validate-data-in-datasets.md)

  - [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)

- Запрос и поиск данных в наборе данных. Дополнительные сведения см. в разделе [наборы данных запросов](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] включает [LINQ (интегрированный в язык запрос)](/dotnet/csharp/linq/) над данными в <xref:System.Data.DataSet> объекте. Дополнительные сведения см. в разделе [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Окно **Источники данных** используется для привязки элементов управления пользовательского интерфейса к набору данных или отдельным столбцам, а также для указания столбцов, изменяемых пользователем. Дополнительные сведения см. [в разделе Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Наборы данных и N-уровневая архитектура

Сведения о наборах данных в многоуровневых приложениях см. в статье [Работа с наборами данных в n-уровневых приложениях](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Наборы данных и XML

Дополнительные сведения о преобразовании наборов данных в XML-код и обратно см. в разделе [чтение XML-информации в наборе данных](../data-tools/read-xml-data-into-a-dataset.md) и [Сохранение набора данных](../data-tools/save-a-dataset-as-xml.md)в формате XML.

## <a name="see-also"></a>См. также

- [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
