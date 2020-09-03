---
title: Наборы данных запросов | Документация Майкрософт
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ccd5deffb0127769e2cd9dff3bf2accf75617eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607437"
---
# <a name="query-datasets"></a>Наборы данных запросов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для поиска конкретных записей в наборе данных используйте метод Финдби в объекте DataTable, напишите собственный цикл foreach по коллекции строк таблицы или используйте [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.

## <a name="dataset-case-sensitivity"></a>Чувствительность к регистру наборов данных
 В наборе данных имена таблиц и столбцов по умолчанию не учитывают регистр, то есть таблица в наборе данных с именем "Customers" также может называться "Customers". Это соответствует соглашениям об именовании во многих базах данных, включая SQL Server.In SQL Server, поведение по умолчанию заключается в том, что имена элементов данных не могут отличаться только регистром.

> [!NOTE]
> В отличие от наборов данных, XML-документы чувствительны к регистру, поэтому имена элементов, определенных в схемах, учитывают регистр. Например, протокол схемы позволяет схеме определить таблицу с именем Customers и другую таблицу с именем Customers. Это может привести к конфликтам имен, если для создания класса набора данных используется схема, содержащая элементы, отличающиеся только регистром.

 Однако чувствительность к регистру может быть фактором, определяющим способ интерпретации данных в наборе данных. Например, при фильтрации данных в таблице набора данных условия поиска могут возвращать различные результаты в зависимости от того, учитывается ли регистр при сравнении. Можно контролировать чувствительность к регистру при фильтрации, поиске и сортировке, устанавливая свойство набора данных <xref:System.Data.DataSet.CaseSensitive%2A> . Все таблицы в наборе данных по умолчанию наследуют значение этого свойства. (Это свойство можно переопределить для каждой отдельной таблицы, задав <xref:System.Data.DataTable.CaseSensitive%2A> свойство таблицы.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Нахождение определенной строки в таблице данных

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Поиск строки в типизированном наборе данных со значением первичного ключа

- Чтобы указать строку, вызовите строго типизированный `FindBy` метод, который использует первичный ключ таблицы.

     В следующем примере `CustomerID` столбец является первичным ключом `Customers` таблицы. Это означает, что созданный `FindBy` метод имеет значение `FindByCustomerID` . В примере показано, как назначить конкретное значение <xref:System.Data.DataRow> переменной с помощью созданного `FindBy` метода.

     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Поиск строки в нетипизированном наборе данных со значением первичного ключа

- Вызовите <xref:System.Data.DataRowCollection.Find%2A> метод <xref:System.Data.DataRowCollection> коллекции, передав первичный ключ в качестве параметра.

     В следующем примере показано, как объявить новую строку с именем `foundRow` и присвоить ей возвращаемое значение <xref:System.Data.DataRowCollection.Find%2A> метода. Если первичный ключ найден, содержимое столбца с индексом 1 отображается в окне сообщения.

     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]

## <a name="findrows-by-column-values"></a>FindRows по значениям столбцов

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Поиск строк на основе значений в любом столбце

- Таблицы данных создаются с помощью <xref:System.Data.DataTable.Select%2A> метода, который возвращает массив <xref:System.Data.DataRow> s на основе выражения, переданного <xref:System.Data.DataTable.Select%2A> методу. Дополнительные сведения о создании допустимых выражений см. в разделе "синтаксис выражений" на странице со сведениями о <xref:System.Data.DataColumn.Expression%2A> свойстве.

     В следующем примере показано, как использовать <xref:System.Data.DataTable.Select%2A> метод объекта <xref:System.Data.DataTable> для размещения конкретных строк.

     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]

## <a name="access-related-records"></a>Доступ к связанным записям
 Если таблицы в наборе данных связаны, <xref:System.Data.DataRelation> объект может сделать связанные записи доступными в другой таблице. Например, можно сделать доступным набор данных, содержащий `Customers` `Orders` таблицы и.

 Объект можно использовать <xref:System.Data.DataRelation> для нахождение связанных записей путем вызова <xref:System.Data.DataRow.GetChildRows%2A> метода <xref:System.Data.DataRow> в родительской таблице. Этот метод возвращает массив связанных дочерних записей. Или можно вызвать <xref:System.Data.DataRow.GetParentRow%2A> метод объекта <xref:System.Data.DataRow> в дочерней таблице. Этот метод возвращает один объект <xref:System.Data.DataRow> из родительской таблицы.

 На этой странице приведены примеры использования типизированных наборов данных. Дополнительные сведения о переходе по связям в нетипизированных наборах данных см. в разделе [Навигация по связям DataRelation](https://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).

> [!NOTE]
> Если вы работаете в Windows Forms приложении и используете функции привязки данных для вывода данных, форма, созданная конструктором, может предоставить достаточно функциональных возможностей для вашего приложения. Дополнительные сведения см. [в разделе Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

 В следующих примерах кода показано, как перемещаться по связям вверх и вниз в типизированных наборах данных. В примерах кода используются типизированные <xref:System.Data.DataRow> s ( `NorthwindDataSet.OrdersRow` ) и созданные `FindBy` методы *PrimaryKey* ( `FindByCustomerID` ) для определения местоположения нужной строки и возврата связанных записей. Примеры компилируются и выполняются правильно, только если у вас есть:

- Экземпляр набора данных `NorthwindDataSet` с именем и `Customers` таблицей.

- `Orders`Таблица.

- Связь с именем `FK_Orders_Customers` , связывающая две таблицы, доступные области кода.

Кроме того, обе таблицы должны быть заполнены данными для любых возвращаемых записей.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Получение дочерних записей выбранной родительской записи

- Вызовите <xref:System.Data.DataRow.GetChildRows%2A> метод определенной `Customers` строки данных и возвратите массив строк из `Orders` таблицы:

     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Возврат родительской записи выбранной дочерней записи

- Вызовите <xref:System.Data.DataRow.GetParentRow%2A> метод определенной `Orders` строки данных и возвратите одну строку из `Customers` таблицы:

     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
