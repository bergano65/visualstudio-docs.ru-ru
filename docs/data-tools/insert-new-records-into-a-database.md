---
title: Вставка новых записей в базу данных
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aaca23e6aa81fab958fc813fa5e2331f8906a562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648317"
---
# <a name="insert-new-records-into-a-database"></a>Вставка новых записей в базу данных

Чтобы вставить новые записи в базу данных, можно использовать метод `TableAdapter.Update` или один из методов DBDirect адаптера таблицы (в частности метод `TableAdapter.Insert`). Дополнительные сведения см. в разделе [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Если приложение не использует адаптеры таблиц TableAdapter, можно использовать объекты команд (например, <xref:System.Data.SqlClient.SqlCommand>) для вставки новых записей в базу данных.

Если приложение использует наборы данных для хранения, используйте метод `TableAdapter.Update`. Метод `Update` отправляет все изменения (обновления, вставки и удаления) в базу данных.

Если приложение использует объекты для хранения данных или требуется более точный контроль над созданием новых записей в базе данных, используйте метод `TableAdapter.Insert`.

Если в TableAdapter нет метода `Insert`, это означает, что адаптер таблицы настроен для использования хранимых процедур или свойство `GenerateDBDirectMethods` имеет значение `false`. Попробуйте задать для свойства `GenerateDBDirectMethods` TableAdapter значение `true` в **Конструктор наборов данных**, а затем сохраните набор данных. Это приведет к повторному формированию TableAdapter. Если TableAdapter по-прежнему не содержит `Insert` метод, то таблица, вероятно, не предоставляет достаточно сведений о схеме для различения отдельных строк (например, в таблице может отсутствовать набор первичных ключей).

## <a name="insert-new-records-by-using-tableadapters"></a>Вставка новых записей с помощью адаптеров таблиц

Адаптеры таблиц предоставляют различные способы вставки новых записей в базу данных в зависимости от требований приложения.

Если приложение использует наборы данных для хранения, можно просто добавить новые записи в нужные <xref:System.Data.DataTable> в наборе данных, а затем вызвать метод `TableAdapter.Update`. Метод `TableAdapter.Update` отправляет любые изменения в <xref:System.Data.DataTable> в базу данных (включая измененные и удаленные записи).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Вставка новых записей в базу данных с помощью метода TableAdapter. Update

1. Добавьте новые записи в нужные <xref:System.Data.DataTable>, создав новый <xref:System.Data.DataRow> и добавив их в коллекцию <xref:System.Data.DataTable.Rows%2A>.

2. После добавления новых строк в <xref:System.Data.DataTable> вызовите метод `TableAdapter.Update`. Объем обновляемых данных можно контролировать путем передачи всего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, массива <xref:System.Data.DataRow>s или одного <xref:System.Data.DataRow>.

   В следующем коде показано, как добавить новую запись в <xref:System.Data.DataTable> и затем вызвать метод `TableAdapter.Update`, чтобы сохранить новую строку в базе данных. (В этом примере используется таблица `Region` в базе данных Northwind.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Вставка новых записей в базу данных с помощью метода TableAdapter. INSERT

Если приложение использует объекты для хранения данных, можно использовать метод `TableAdapter.Insert` для создания новых строк непосредственно в базе данных. Метод `Insert` принимает отдельные значения для каждого столбца в качестве параметров. При вызове метода в базу данных вставляется новая запись с передаваемыми значениями параметров.

- Вызовите метод `Insert` TableAdapter, передав значения для каждого столбца в качестве параметров.

В следующей процедуре показано использование метода `TableAdapter.Insert` для вставки строк. В этом примере данные вставляются в таблицу `Region` базы данных Northwind.

> [!NOTE]
> Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Вставка новых записей с помощью командных объектов

Новые записи можно вставлять непосредственно в базу данных с помощью командных объектов.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Вставка новых записей в базу данных с помощью командных объектов

- Создайте новый объект Command, а затем задайте его свойства `Connection`, `CommandType` и `CommandText`.

В следующем примере демонстрируется вставка записей в базу данных с помощью командного объекта. Данные вставляются в таблицу `Region` базы данных Northwind.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>Безопасность в .NET

Необходимо иметь доступ к базе данных, к которой вы пытаетесь подключиться, а также разрешение на выполнение вставки в нужную таблицу.

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)