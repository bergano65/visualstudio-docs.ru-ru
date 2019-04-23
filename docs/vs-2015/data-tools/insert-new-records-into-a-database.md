---
title: Вставка новых записей в базу данных | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 001f3a3c74f792fbe3028b6915cb350d359221a1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043140"
---
# <a name="insert-new-records-into-a-database"></a>Вставка новых записей в базу данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для вставки новых записей в базу данных, можно использовать `TableAdapter.Update` метода или одного из методов DBDirect адаптера таблицы (в частности `TableAdapter.Insert` метод).
  
 Если приложение не использует адаптеры таблиц, можно использовать командные объекты (например, <xref:System.Data.SqlClient.SqlCommand>) для вставки новых записей в базе данных.  
  
 Если приложение использует наборы данных для хранения данных, используйте `TableAdapter.Update` метод. `Update` Метод отправляет все изменения (обновления, вставки и удаления) в базу данных.  
  
 Если приложение использует объекты для хранения данных, или если требуется детальный контроль над созданием новых записей в базе данных, используйте `TableAdapter.Insert` метод.  
  
 Если нет TableAdapter `Insert` метода, это означает, что либо TableAdapter настроен с помощью хранимых процедур или его `GenerateDBDirectMethods` свойству `false`. Попробуйте задать TableAdapter `GenerateDBDirectMethods` свойства `true` из конструктора наборов данных, а затем сохраните набор данных. Это приведет к повторному созданию адаптера таблицы. Если адаптер таблицы не имеет `Insert` метод, а затем таблицы, вероятно, не предоставляет достаточно сведений о схеме для различения отдельных строк (например, может существовать без основной набор ключей в таблице).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Вставка новых записей с помощью адаптера таблицы  
 Адаптеры таблиц предоставляют различные способы вставки новых записей в базу данных, в зависимости от требований приложения.  
  
 Если приложение использует наборы данных для хранения данных, то можно просто добавлять данные в нужные <xref:System.Data.DataTable> в набор данных, а затем вызовите метод `TableAdapter.Update` метод. `TableAdapter.Update` Метод отправляет все изменения <xref:System.Data.DataTable> к базе данных (включая измененные и удаленные записи).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Для вставки новых записей в базу данных с помощью TableAdapter.Update-метод  
  
1. Добавление новых записей в нужные <xref:System.Data.DataTable> путем создания нового <xref:System.Data.DataRow> и добавления его в <xref:System.Data.DataTable.Rows%2A> коллекции. Дополнительные сведения см. в разделе [Как Добавление строк в объект DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).  
  
2. После добавления новых строк <xref:System.Data.DataTable>, вызовите `TableAdapter.Update` метод. Можно управлять объемом данных для обновления путем передачи всего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, массив <xref:System.Data.DataRow>s или одной <xref:System.Data.DataRow>.  
  
    Ниже показано, как добавить новую запись для <xref:System.Data.DataTable> , а затем вызвать `TableAdapter.Update` метод для сохранения новой строки в базу данных. (В этом примере используется `Region` таблицы в базе данных "Борей".)  
  
    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]  
  
   Если приложение использует объекты для хранения данных, можно использовать `TableAdapter.Insert` метод для создания новых строк непосредственно в базе данных. `Insert` Метод принимает отдельные значения для каждого столбца в качестве параметров. Вызов метода вставляет новую запись в базу данных с помощью значений, передаваемых параметров.  
  
   В следующей процедуре используется `Region` таблицы в базе данных "Борей" в качестве примера.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Для вставки новых записей в базу данных с помощью TableAdapter.INSERT-метод  
  
- Вызов метода `Insert` метод, передав значения для каждого столбца в качестве параметров.  
  
    > [!NOTE]
    >  Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Вставка новых записей с помощью командных объектов  
 Следующий пример вставляет новые записи непосредственно в базу данных с помощью объектов команд.
  
 В следующей процедуре используется `Region` таблицы в базе данных "Борей" в качестве примера.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Для вставки новых записей в базу данных с помощью командных объектов  
  
- Создать новый командный объект и задайте его `Connection`, `CommandType`, и `CommandText` свойства.  
  
     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Необходимо иметь доступ для базы данных, которую вы пытаетесь подключиться, а также разрешение на вставку в нужную таблицу.  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
