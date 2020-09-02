---
title: Вставить новые записи в базу данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c686a764f42f50a3e59da3e8b37b219ddb7b11c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651561"
---
# <a name="insert-new-records-into-a-database"></a>Вставка новых записей в базу данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы вставить новые записи в базу данных, можно использовать `TableAdapter.Update` метод или один из методов DBDirect адаптера таблицы (в частности, `TableAdapter.Insert` метод).

 Если приложение не использует адаптеры таблиц, можно использовать объекты команд (например,  <xref:System.Data.SqlClient.SqlCommand> ) для вставки новых записей в базу данных.

 Если приложение использует наборы данных для хранения, используйте `TableAdapter.Update` метод. `Update`Метод отправляет все изменения (обновления, вставки и удаления) в базу данных.

 Если приложение использует объекты для хранения данных или требуется более точный контроль над созданием новых записей в базе данных, используйте `TableAdapter.Insert` метод.

 Если в TableAdapter нет `Insert` метода, это означает, что адаптер таблицы настроен для использования хранимых процедур или его `GenerateDBDirectMethods` свойство имеет значение `false` . Попробуйте задать `GenerateDBDirectMethods` для свойства TableAdapter значение `true` from в конструктор наборов данных, а затем сохраните набор данных. Это приведет к повторному формированию TableAdapter. Если TableAdapter по-прежнему не имеет `Insert` метода, то таблица, вероятно, не предоставляет достаточно сведений о схеме для различения отдельных строк (например, в таблице может отсутствовать набор первичных ключей).

## <a name="insert-new-records-by-using-tableadapters"></a>Вставка новых записей с помощью адаптеров таблиц
 Адаптеры таблиц предоставляют различные способы вставки новых записей в базу данных в зависимости от требований приложения.

 Если приложение использует наборы данных для хранения, можно просто добавить новые записи в нужный <xref:System.Data.DataTable> набор данных, а затем вызвать `TableAdapter.Update` метод. `TableAdapter.Update`Метод отправляет любые изменения в <xref:System.Data.DataTable> базу данных (включая измененные и удаленные записи).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Вставка новых записей в базу данных с помощью метода TableAdapter. Update

1. Добавьте новые записи в нужное расположение <xref:System.Data.DataTable> , создав новый объект <xref:System.Data.DataRow> и добавив его в <xref:System.Data.DataTable.Rows%2A> коллекцию. Дополнительные сведения см. [в разделе инструкции. Добавление строк в таблицу](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf)данных.

2. После добавления новых строк в <xref:System.Data.DataTable> вызовите `TableAdapter.Update` метод. Можно управлять объемом обновляемых данных, передавая целое число <xref:System.Data.DataSet> , а <xref:System.Data.DataTable> , массив из <xref:System.Data.DataRow> s или один <xref:System.Data.DataRow> .

    В следующем коде показано, как добавить новую запись в, <xref:System.Data.DataTable> а затем вызвать метод, `TableAdapter.Update` чтобы сохранить новую строку в базе данных. (В этом примере используется `Region` Таблица в базе данных Northwind.)

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Если приложение использует объекты для хранения данных, можно использовать `TableAdapter.Insert` метод для создания новых строк непосредственно в базе данных. `Insert`Метод принимает отдельные значения для каждого столбца в качестве параметров. При вызове метода в базу данных вставляется новая запись с передаваемыми значениями параметров.

   В следующей процедуре в `Region` качестве примера используется таблица в базе данных Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Вставка новых записей в базу данных с помощью метода TableAdapter. INSERT

- Вызовите метод TableAdapter `Insert` , передав значения для каждого столбца в качестве параметров.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Вставка новых записей с помощью командных объектов
 В следующем примере новые записи вставляются непосредственно в базу данных с помощью командных объектов.

 В следующей процедуре в `Region` качестве примера используется таблица в базе данных Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Вставка новых записей в базу данных с помощью командных объектов

- Создайте новый объект Command и задайте его `Connection` `CommandType` свойства, и `CommandText` .

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>Безопасность .NET Framework
 Необходимо иметь доступ к базе данных, к которой вы пытаетесь подключиться, а также разрешение на выполнение вставки в нужную таблицу.

## <a name="see-also"></a>См. также:
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
