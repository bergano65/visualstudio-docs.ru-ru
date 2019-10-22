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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651561"
---
# <a name="insert-new-records-into-a-database"></a>Вставка новых записей в базу данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы вставить новые записи в базу данных, можно использовать метод `TableAdapter.Update` или один из методов DBDirect адаптера таблицы (в частности метод `TableAdapter.Insert`).

 Если приложение не использует адаптеры таблиц TableAdapter, можно использовать объекты команд (например, <xref:System.Data.SqlClient.SqlCommand>) для вставки новых записей в базу данных.

 Если приложение использует наборы данных для хранения, используйте метод `TableAdapter.Update`. Метод `Update` отправляет все изменения (обновления, вставки и удаления) в базу данных.

 Если приложение использует объекты для хранения данных или требуется более точный контроль над созданием новых записей в базе данных, используйте метод `TableAdapter.Insert`.

 Если в TableAdapter нет метода `Insert`, это означает, что адаптер таблицы настроен для использования хранимых процедур или свойство `GenerateDBDirectMethods` имеет значение `false`. Попробуйте задать для свойства `GenerateDBDirectMethods` TableAdapter значение `true` в конструктор наборов данных, а затем сохраните набор данных. Это приведет к повторному формированию TableAdapter. Если TableAdapter по-прежнему не имеет `Insert` метода, то таблица, вероятно, не предоставляет достаточно сведений о схеме для различения отдельных строк (например, в таблице может отсутствовать первичный ключ).

## <a name="insert-new-records-by-using-tableadapters"></a>Вставка новых записей с помощью адаптеров таблиц
 Адаптеры таблиц предоставляют различные способы вставки новых записей в базу данных в зависимости от требований приложения.

 Если приложение использует наборы данных для хранения, можно просто добавить новые записи в нужный <xref:System.Data.DataTable> в наборе данных, а затем вызвать метод `TableAdapter.Update`. Метод `TableAdapter.Update` отправляет любые изменения в <xref:System.Data.DataTable> в базу данных (включая измененные и удаленные записи).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Вставка новых записей в базу данных с помощью метода TableAdapter. Update

1. Добавьте новые записи в нужные <xref:System.Data.DataTable>, создав новый <xref:System.Data.DataRow> и добавив их в коллекцию <xref:System.Data.DataTable.Rows%2A>. Дополнительные сведения см. [в разделе инструкции. Добавление строк в таблицу](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf)данных.

2. После добавления новых строк в <xref:System.Data.DataTable> вызовите метод `TableAdapter.Update`. Объем обновляемых данных можно контролировать путем передачи всего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, массива <xref:System.Data.DataRow>s или одного <xref:System.Data.DataRow>.

    В следующем коде показано, как добавить новую запись в <xref:System.Data.DataTable> и затем вызвать метод `TableAdapter.Update`, чтобы сохранить новую строку в базе данных. (В этом примере используется таблица `Region` в базе данных Northwind.)

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Если приложение использует объекты для хранения данных, можно использовать метод `TableAdapter.Insert` для создания новых строк непосредственно в базе данных. Метод `Insert` принимает отдельные значения для каждого столбца в качестве параметров. При вызове метода в базу данных вставляется новая запись с передаваемыми значениями параметров.

   В следующей процедуре в качестве примера используется таблица `Region` в базе данных Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Вставка новых записей в базу данных с помощью метода TableAdapter. INSERT

- Вызовите метод `Insert` TableAdapter, передав значения для каждого столбца в качестве параметров.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Вставка новых записей с помощью командных объектов
 В следующем примере новые записи вставляются непосредственно в базу данных с помощью командных объектов.

 В следующей процедуре в качестве примера используется таблица `Region` в базе данных Northwind.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Вставка новых записей в базу данных с помощью командных объектов

- Создайте новый объект Command, а затем задайте его свойства `Connection`, `CommandType` и `CommandText`.

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>Безопасность платформы .NET Framework
 Необходимо иметь доступ к базе данных, к которой вы пытаетесь подключиться, а также разрешение на выполнение вставки в нужную таблицу.

## <a name="see-also"></a>См. также раздел
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
