---
title: 'Практическое: удаление записей в базе данных | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: aff5a67d54376488ccce2bca5dd67b84d6c73949
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210188"
---
# <a name="how-to-delete-records-in-a-database"></a>Практическое руководство. Удаление записей из базы данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы удалить записи из базы данных, используйте `TableAdapter.Update` метод или `TableAdapter.Delete` метод. Или, если приложение не использует адаптеры таблиц, можно использовать командные объекты для удаления записей из базы данных (например, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
 `TableAdapter.Update` Метод обычно используется, если приложение использует наборы данных для хранения данных, тогда как `TableAdapter.Delete` метод обычно используется, если приложение использует объекты для хранения данных.  
  
 Если TableAdapter имеет `Delete` метода, это означает либо TableAdapter настроен с помощью хранимых процедур или его `GenerateDBDirectMethods` свойству `false`. Попробуйте задать TableAdapter `GenerateDBDirectMethods` свойства `true` изнутри [конструктор наборов данных](../data-tools/creating-and-editing-typed-datasets.md) и затем сохраните набор данных для повторного создания адаптера таблицы. Если TableAdapter по-прежнему имеет `Delete` метод, а затем таблицы, вероятно, не предоставляет достаточно сведений о схеме для различения отдельных строк (например, первичный ключ не имеет значение в таблице).  
  
## <a name="delete-records-using-tableadapters"></a>Удаление записей с помощью адаптеров таблиц  
 Адаптеры таблиц предоставляют различные способы удаления записей из базы данных в зависимости от требований приложения.  
  
 Если приложение использует наборы данных для хранения данных можно просто удалить записи из нужной <xref:System.Data.DataTable> в <xref:System.Data.DataSet>, а затем вызвать `TableAdapter.Update` метод. `TableAdapter.Update` Метод принимает любые изменения в таблице данных и отправляет эти изменения к базе данных (включая вставленных, обновленных и удаленных записей).  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>Для удаления записей из базы данных, использующей TableAdapter.Update-метод  
  
-   Удаление записей из нужной <xref:System.Data.DataTable> , удалив <xref:System.Data.DataRow> объекты из таблицы. Дополнительные сведения см. в разделе [как: удаление строк в таблице DataTable](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e). После строки удаляются из <xref:System.Data.DataTable>, вызовите `TableAdapter.Update` метод. Можно управлять объемом данных для обновления путем передачи всего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, массив <xref:System.Data.DataRow>s или одной <xref:System.Data.DataRow>. Ниже показано, как удалить запись <xref:System.Data.DataTable> , а затем вызвать `TableAdapter.Update` метод для передачи изменения и удаления строки из базы данных. (В этом примере базы данных Northwind `Region` таблицы.)  
  
     [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
     [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
 Если приложение использует объекты для хранения данных в приложении, можно использовать методы DBDirect адаптера таблицы для удаления данных непосредственно из базы данных. Вызов `Delete` метод удаляет записи из базы данных на основе значений параметров, переданный.  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>Для удаления записей из базы данных, использующей TableAdapter.DELETE-метод  
  
-   Вызов метода `Delete` метод, передав значения для каждого столбца в качестве параметров `Delete` метод. (В этом примере базы данных Northwind `Region` таблицы.)  
  
    > [!NOTE]
    >  Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>Удаление записей с помощью командных объектов  
 Следующий пример удаляет записи непосредственно из базы данных с помощью командных объектов. Дополнительные сведения об использовании объектов command для выполнения команд и хранимых процедур см. в разделе [выборка данных в приложении](../data-tools/fetching-data-into-your-application.md).  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>Для удаления записей из базы данных с помощью командных объектов  
  
-   Создайте новый объект команды, установите его `Connection`, `CommandType`, и `CommandText` свойства. (В этом примере базы данных Northwind `Region` таблицы.)  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Необходимо иметь доступ для базы данных, которую вы пытаетесь подключиться, а также разрешение на удаление записей из нужной таблицы.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о TableAdapter](../data-tools/tableadapter-overview.md)   
 [Вставка новых записей в базу данных](../data-tools/insert-new-records-into-a-database.md)   
 [Практическое: обновление записей в базе данных](../data-tools/how-to-update-records-in-a-database.md)   
 [Сохранение данных из объекта в базе данных](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Общие сведения о данных приложений в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)