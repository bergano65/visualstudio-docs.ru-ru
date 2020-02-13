---
title: Наборы данных запросов
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4080866de58e17c5e11ed01d61740c2f83aed9a7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586345"
---
# <a name="query-datasets"></a>Наборы данных запросов
Для поиска конкретных записей в наборе данных используйте метод `FindBy` в объекте DataTable, напишите собственную инструкцию foreach для циклической обработки коллекции строк таблицы или используйте [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Чувствительность к регистру наборов данных
В наборе данных имена таблиц и столбцов по умолчанию не учитывают регистр, то есть таблица в наборе данных с именем "Customers" также может называться "Customers". Это соответствует соглашениям об именовании во многих базах данных, включая SQL Server. В SQL Server поведение по умолчанию заключается в том, что имена элементов данных не могут отличаться только регистром.

> [!NOTE]
> В отличие от наборов данных, XML-документы чувствительны к регистру, поэтому имена элементов, определенных в схемах, учитывают регистр. Например, протокол схемы позволяет схеме определить таблицу с именем Customers и другую таблицу с именем Customers. Это может привести к конфликтам имен, если для создания класса набора данных используется схема, содержащая элементы, отличающиеся только регистром.

Однако чувствительность к регистру может быть фактором, определяющим способ интерпретации данных в наборе данных. Например, при фильтрации данных в таблице набора данных условия поиска могут возвращать различные результаты в зависимости от того, учитывается ли регистр при сравнении. Можно контролировать чувствительность к регистру при фильтрации, поиске и сортировке, устанавливая свойство <xref:System.Data.DataSet.CaseSensitive%2A> набора данных. Все таблицы в наборе данных по умолчанию наследуют значение этого свойства. (Это свойство можно переопределить для каждой отдельной таблицы, задав свойство <xref:System.Data.DataTable.CaseSensitive%2A> таблицы.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Нахождение определенной строки в таблице данных

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Поиск строки в типизированном наборе данных со значением первичного ключа

- Чтобы указать строку, вызовите строго типизированный метод `FindBy`, использующий первичный ключ таблицы.

     В следующем примере столбец `CustomerID` является первичным ключом `Customers` таблицы. Это означает, что созданный метод `FindBy` `FindByCustomerID`. В примере показано, как назначить определенную <xref:System.Data.DataRow> переменной с помощью созданного метода `FindBy`.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Поиск строки в нетипизированном наборе данных со значением первичного ключа

- Вызовите метод <xref:System.Data.DataRowCollection.Find%2A> коллекции <xref:System.Data.DataRowCollection>, передав первичный ключ в качестве параметра.

     В следующем примере показано, как объявить новую строку с именем `foundRow` и присвоить ей возвращаемое значение метода <xref:System.Data.DataRowCollection.Find%2A>. Если первичный ключ найден, содержимое столбца с индексом 1 отображается в окне сообщения.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Поиск строк по значениям столбцов

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Поиск строк на основе значений в любом столбце

- Таблицы данных создаются с помощью метода <xref:System.Data.DataTable.Select%2A>, который возвращает массив <xref:System.Data.DataRow>s на основе выражения, переданного методу <xref:System.Data.DataTable.Select%2A>. Дополнительные сведения о создании допустимых выражений см. в разделе "синтаксис выражений" страницы о свойстве <xref:System.Data.DataColumn.Expression%2A>.

     В следующем примере показано, как использовать метод <xref:System.Data.DataTable.Select%2A> <xref:System.Data.DataTable> для нахождение конкретных строк.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Доступ к связанным записям
Если таблицы в наборе данных связаны, объект <xref:System.Data.DataRelation> может сделать связанные записи доступными в другой таблице. Например, можно сделать доступным набор данных, содержащий `Customers` и `Orders` таблицы.

Объект <xref:System.Data.DataRelation> можно использовать для нахождение связанных записей путем вызова метода <xref:System.Data.DataRow.GetChildRows%2A> <xref:System.Data.DataRow> в родительской таблице. Этот метод возвращает массив связанных дочерних записей. Или можно вызвать метод <xref:System.Data.DataRow.GetParentRow%2A> <xref:System.Data.DataRow> в дочерней таблице. Этот метод возвращает один <xref:System.Data.DataRow> из родительской таблицы.

На этой странице приведены примеры использования типизированных наборов данных. Дополнительные сведения о переходе по связям в нетипизированных наборах данных см. в разделе [Навигация по связям DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Если вы работаете в Windows Forms приложении и используете функции привязки данных для вывода данных, форма, созданная конструктором, может предоставить достаточно функциональных возможностей для вашего приложения. Дополнительные сведения см. [в разделе Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). В частности, см. раздел [связи в наборах данных](relationships-in-datasets.md).

В следующих примерах кода показано, как перемещаться по связям вверх и вниз в типизированных наборах данных. В примерах кода используются типизированные <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) и созданные методы Финдби*PrimaryKey* (`FindByCustomerID`) для нахождение нужной строки и возврата связанных записей. Примеры компилируются и выполняются правильно, только если у вас есть:

- Экземпляр набора данных с именем `NorthwindDataSet` с таблицей `Customers`.

- Таблица `Orders`.

- Связь с именем `FK_Orders_Customers`, связывающая две таблицы.

Кроме того, обе таблицы должны быть заполнены данными для любых возвращаемых записей.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Получение дочерних записей выбранной родительской записи

- Вызовите метод <xref:System.Data.DataRow.GetChildRows%2A> определенной строки данных `Customers` и возвратите массив строк из таблицы `Orders`:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Возврат родительской записи выбранной дочерней записи

- Вызовите метод <xref:System.Data.DataRow.GetParentRow%2A> определенной строки данных `Orders` и возвратите одну строку из таблицы `Customers`:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>См. также:

- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
