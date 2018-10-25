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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aae5ec2197ff2a899f27df20e7199fdeb7a02d31
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949205"
---
# <a name="insert-new-records-into-a-database"></a>Вставка новых записей в базу данных

Для вставки новых записей в базу данных, можно использовать `TableAdapter.Update` метода или одного из методов DBDirect адаптера таблицы (в частности `TableAdapter.Insert` метод). Дополнительные сведения см. в разделе [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Если приложение не использует адаптеры таблиц, можно использовать командные объекты (например, <xref:System.Data.SqlClient.SqlCommand>) для вставки новых записей в базе данных.

Если приложение использует наборы данных для хранения данных, используйте `TableAdapter.Update` метод. `Update` Метод отправляет все изменения (обновления, вставки и удаления) в базу данных.

Если приложение использует объекты для хранения данных, или если требуется детальный контроль над созданием новых записей в базе данных, используйте `TableAdapter.Insert` метод.

Если нет TableAdapter `Insert` метода, это означает, что либо TableAdapter настроен с помощью хранимых процедур или его `GenerateDBDirectMethods` свойству `false`. Попробуйте задать TableAdapter `GenerateDBDirectMethods` свойства `true` изнутри **конструктор наборов данных**, а затем сохраните набор данных. Это приведет к повторному созданию адаптера таблицы. Если адаптер таблицы не имеет `Insert` метод, таблицы, вероятно, не предоставляет достаточно сведений о схеме для различения отдельных строк (например, может существовать без основной набор ключей в таблице).

## <a name="insert-new-records-by-using-tableadapters"></a>Вставка новых записей с помощью адаптера таблицы

Адаптеры таблиц предоставляют различные способы вставки новых записей в базу данных, в зависимости от требований приложения.

Если приложение использует наборы данных для хранения данных, можно просто добавлять данные в нужные <xref:System.Data.DataTable> в набор данных, а затем вызовите метод `TableAdapter.Update` метод. `TableAdapter.Update` Метод отправляет все изменения <xref:System.Data.DataTable> к базе данных (включая измененные и удаленные записи).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Для вставки новых записей в базу данных с помощью TableAdapter.Update-метод

1. Добавление новых записей в нужные <xref:System.Data.DataTable> путем создания нового <xref:System.Data.DataRow> и добавления его в <xref:System.Data.DataTable.Rows%2A> коллекции.

2. После добавления новых строк <xref:System.Data.DataTable>, вызовите `TableAdapter.Update` метод. Можно управлять объемом данных для обновления путем передачи всего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, массив <xref:System.Data.DataRow>s или одной <xref:System.Data.DataRow>.

   Ниже показано, как добавить новую запись для <xref:System.Data.DataTable> , а затем вызвать `TableAdapter.Update` метод для сохранения новой строки в базу данных. (В этом примере используется `Region` таблицы в базе данных "Борей".)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Для вставки новых записей в базу данных с помощью TableAdapter.INSERT-метод

Если приложение использует объекты для хранения данных, можно использовать `TableAdapter.Insert` метод для создания новых строк непосредственно в базе данных. `Insert` Метод принимает отдельные значения для каждого столбца в качестве параметров. Вызов метода вставляет новую запись в базу данных с помощью значений, передаваемых параметров.

- Вызов метода `Insert` метод, передав значения для каждого столбца в качестве параметров.

В следующей процедуре показано использование `TableAdapter.Insert` метод для вставки строк. Этот пример вставляет данные в `Region` таблицы в базе данных "Борей".

> [!NOTE]
> Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Вставка новых записей с помощью командных объектов

Можно вставлять новые записи непосредственно в базу данных с помощью объектов команд.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Для вставки новых записей в базу данных с помощью командных объектов

- Создать новый командный объект и задайте его `Connection`, `CommandType`, и `CommandText` свойства.

В следующем примере показано вставку записей в базу данных с помощью объекта команды. Он вставляет данные в `Region` таблицы в базе данных "Борей".

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>безопасность платформы .NET Framework

Необходимо иметь доступ для базы данных, которую вы пытаетесь подключиться, а также разрешение на вставку в нужную таблицу.

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)