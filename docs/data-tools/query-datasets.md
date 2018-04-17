---
title: Запрос наборов данных | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f2d3ca534783b8178f14a4121a46e2552221ab92
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="query-datasets"></a>Наборы данных запросов
Для поиска определенных записей в наборе данных, вызовите метод FindBy DataTable, написать собственные оператора foreach для циклического прохода по коллекции строк таблицы, или используйте [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
## <a name="dataset-case-sensitivity"></a>Чувствительность к регистру набора данных  
В наборе данных, имена таблиц и столбцов не учитывается регистр, по умолчанию — то есть таблицы в набор данных с именем «Заказчики» может также называться «customers». Это соответствует соглашения об именовании в несколько баз данных, включая SQL Server. В SQL Server по умолчанию — что имена элементов данных должны отличаться только регистром.  
  
> [!NOTE]
>  В отличие от наборов данных XML-документов учитывают регистр, поэтому имена элементов данных, определенные в схемах чувствительны к регистру. Например протокол схемы позволяет определить таблицу с именем «Заказчики» и другой таблицей с именем «customers». Это может привести к конфликтов имен, если схему, которая содержит элементы, отличающиеся только регистром используется для создания класса набора данных.  
  
Чувствительность к регистру, однако может быть фактором способ интерпретации данных в наборе данных. Например при фильтрации данных в таблице набора данных критерий поиска может возвращать различные результаты в зависимости от того, при сравнении учитывается регистр. Чувствительность к регистру, фильтрации, поиска и сортировки с помощью свойства набора данных можно управлять <xref:System.Data.DataSet.CaseSensitive%2A> свойство. Все таблицы в наборе данных наследуют значение этого свойства по умолчанию. (Можно переопределить это свойство для каждой отдельной таблицы, установив в таблице <xref:System.Data.DataTable.CaseSensitive%2A> свойство.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Поиск конкретной строки в таблице данных  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Чтобы найти строку в типизированный набор данных со значением первичного ключа  
  
-   Чтобы найти строки, вызовите строго типизированный `FindBy` метод, который использует первичный ключ таблицы.  
  
     В следующем примере `CustomerID` столбец является первичным ключом `Customers` таблицы. Это означает, что созданный `FindBy` метод `FindByCustomerID`. В примере показано присвоить определенный <xref:System.Data.DataRow> переменной с помощью созданного `FindBy` метод.  
  
     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Чтобы найти строку в нетипизированный набор данных со значением первичного ключа  
  
-   Вызовите <xref:System.Data.DataRowCollection.Find%2A> метод <xref:System.Data.DataRowCollection> коллекции, передавая первичный ключ в качестве параметра.  
  
     Следующий пример показывает, как объявить новую строку с именем `foundRow` и назначьте его возвращаемое значение <xref:System.Data.DataRowCollection.Find%2A> метод. Если первичный ключ найден, содержимое индекса столбца 1 отображаются в окне сообщения.  
  
     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]  
  
## <a name="find-rows-by-column-values"></a>Поиск строк по значениям столбцов  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Чтобы найти строки на основе значений в любом столбце  
  
-   Таблицы данных создаются с <xref:System.Data.DataTable.Select%2A> метод, возвращающий массив <xref:System.Data.DataRow>s на основе выражения, передаваемый <xref:System.Data.DataTable.Select%2A> метод. Дополнительные сведения о создании допустимых выражений содержатся в разделе «Синтаксис выражения» страницы <xref:System.Data.DataColumn.Expression%2A> свойство.  
  
     В следующем примере показано, как использовать <xref:System.Data.DataTable.Select%2A> метод <xref:System.Data.DataTable> для поиска конкретных строк.  
  
     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]  
  
## <a name="access-related-records"></a>Записей, связанных с доступом к  
Если таблицы в наборе данных связаны, <xref:System.Data.DataRelation> объекта можно освободить связанных записей в другой таблице. Например, набор данных, содержащий `Customers` и `Orders` таблицы могут быть сделаны доступными.  
  
Можно использовать <xref:System.Data.DataRelation> объект для поиска связанных записей путем вызова <xref:System.Data.DataRow.GetChildRows%2A> метод <xref:System.Data.DataRow> в родительской таблице. Этот метод возвращает массив связанных дочерних записей. Или можно вызвать <xref:System.Data.DataRow.GetParentRow%2A> метод <xref:System.Data.DataRow> в дочерней таблице. Этот метод возвращает один <xref:System.Data.DataRow> из родительской таблицы.  
  
Эта страница содержит примеры использования типизированных наборов данных. Сведения о перемещении отношений в нетипизированные наборы данных см. в разделе [перехода отношений DataRelation](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).  
  
> [!NOTE]
>  Если вы работаете в приложении Windows Forms и использование функций привязки к данным для отображения данных, автоматически созданный конструктором форм может обеспечить достаточную функциональность для вашего приложения. Дополнительные сведения см. в разделе [привязки элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). В частности, в разделе [отношения в наборах данных](relationships-in-datasets.md).  
  
В следующем примере кода показано, как для перемещения вверх и вниз связей в типизированных наборах данных. Использование примеров кода типизированного <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) и созданный FindBy*PrimaryKey* (`FindByCustomerID`) методы для поиска нужной строки и возврата связанных записей. Примеры компилируются и работают только в том случае, если у вас есть:  
  
-   Экземпляр набора данных с именем `NorthwindDataSet` с `Customers` таблицы.  
  
-   `Orders` Таблицы.  
  
-   Связь с именем `FK_Orders_Customers`связи двух таблиц.  
  
Кроме того обе таблицы должны заполняться данными записи, должны быть возвращены.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Для возврата дочерних записей выбранной родительской записи  
  
-   Вызовите <xref:System.Data.DataRow.GetChildRows%2A> метод конкретного `Customers` данных строки и возвращает массив строк из `Orders` таблицы:  
  
     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Для возврата родительской записи выбранной дочерней записи  
  
-   Вызовите <xref:System.Data.DataRow.GetParentRow%2A> метод конкретного `Orders` строку данных и возвращают один строка из `Customers` таблицы:  
  
     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>См. также
[Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  