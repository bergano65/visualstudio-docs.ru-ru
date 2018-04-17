---
title: Вставка новых записей в базу данных | Документы Microsoft
ms.custom: ''
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
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ec7676022d6eefb07ab2d818bc28a772df433297
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="insert-new-records-into-a-database"></a>Вставка новых записей в базе данных
Для вставки новых записей в базу данных, можно использовать `TableAdapter.Update` метода или одного из методов DBDirect адаптера таблицы (в частности `TableAdapter.Insert` метода). Дополнительные сведения см. в разделе [TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
 Если приложение не использует адаптеры таблиц, можно использовать командные объекты (например, <xref:System.Data.SqlClient.SqlCommand>) для вставки новых записей в базе данных.
  
 Если приложение использует наборы данных для хранения данных, используйте `TableAdapter.Update` метод. `Update` Метод отправляет все изменения (обновления, вставки и удаления) в базу данных.  
  
 Если приложение использует объекты для хранения данных, или если требуется детальный контроль над созданием новых записей в базе данных, используйте `TableAdapter.Insert` метод.  
  
 Если TableAdapter не имеет `Insert` метода, это означает, что либо TableAdapter настроен на использование сохраненных процедур или его `GenerateDBDirectMethods` свойству `false`. Попробуйте установить его `GenerateDBDirectMethods` свойства `true` изнутри **конструктора наборов данных**, а затем сохраните набор данных. Это приведет к повторному созданию адаптера таблицы. Если адаптер таблицы не имеет `Insert` метод, то таблица, скорее всего, не предоставляет достаточно сведений о схеме для различения отдельных строк (например, может существовать без основной набор ключей в таблице).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Вставка новых записей с помощью адаптера таблицы  
 Адаптеры таблиц предоставляют различные способы вставки новых записей в базе данных, в зависимости от требований приложения.  
  
 Если приложение использует наборы данных для хранения данных, то можно просто добавлять данные в нужную таблицу <xref:System.Data.DataTable> в наборе данных, а затем вызовите `TableAdapter.Update` метод. `TableAdapter.Update` Метод отправляет все изменения <xref:System.Data.DataTable> в базу данных (включая измененные и удаленные записи).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Для вставки новых записей в базу данных с помощью TableAdapter.Update-метод  
  
1.  Добавление новых записей в нужные <xref:System.Data.DataTable> путем создания нового <xref:System.Data.DataRow> и его добавления в <xref:System.Data.DataTable.Rows%2A> коллекции. 
  
2.  После добавления новых строк в <xref:System.Data.DataTable>, вызовите `TableAdapter.Update` метод. Можно контролировать объем данных для обновления путем передачи всего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, массив <xref:System.Data.DataRow>s или одной <xref:System.Data.DataRow>.  
  
 Ниже показано, как добавить новую запись для <xref:System.Data.DataTable> и затем вызвать `TableAdapter.Update` метод для сохранения новой строки в базу данных. (В этом примере используется `Region` таблицы в базе данных "Борей".)  
  
 [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
 [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Для вставки новых записей в базу данных с помощью TableAdapter.Insert-метод  
Если приложение использует объекты для хранения данных, можно использовать `TableAdapter.Insert` метод для создания новых строк непосредственно в базе данных. `Insert` Метод принимает отдельные значения для каждого столбца в качестве параметров. Вызов метода вставляет новую запись в базу данных с переданные значения параметров.  
  
- Вызов метода `Insert` метод, передав значения для каждого столбца в качестве параметров.  

 В следующей процедуре показано использование `TableAdapter.Insert` метода для вставки строк. В этом примере вставляет данные в `Region` таблицы в базе данных "Борей".  
  
 > [!NOTE]
 >  Если экземпляра нет, создайте экземпляр адаптера таблицы, которые вы хотите использовать.  
  
 [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
 [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Вставка новых записей с помощью командных объектов  
Можно вставлять новые записи непосредственно в базу данных с помощью командных объектов.    
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Для вставки новых записей в базу данных с помощью командных объектов  
  
-   Создание объекта команды и установите его `Connection`, `CommandType`, и `CommandText` свойства.  

 В следующем примере показано вставку записей в базу данных с помощью объекта команды. Он вставляет данные в `Region` таблицы в базе данных "Борей".
  
 [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
 [!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Необходимо иметь доступ для базы данных, которую вы пытаетесь подключиться, а также разрешение на вставку записей в нужную таблицу.  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)