---
title: 'Практическое: обновление записей в базе данных | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
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
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 73ca33f9fb30a178addab6dee136d3b441bd81d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558148"
---
# <a name="how-to-update-records-in-a-database"></a>Практическое руководство. Обновление записей в базе данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно использовать `TableAdapter.Update` метод для обновления (изменения) записей в базе данных. `TableAdapter.Update` Метод предоставляет несколько перегрузок, которые выполняют различные операции в зависимости от передаваемых параметров. Важно понимать результаты вызова различных сигнатур метода.  
  
> [!NOTE]
>  Если приложение не использует адаптеры таблиц, то можно использовать командные объекты для обновления записей в базе данных (например, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>). Дополнительные сведения об обновлении данных с помощью объектов команд см. в разделе «Обновление записей с помощью командных объектов» ниже.  
  
 В следующей таблице описаны поведение различных `TableAdapter.Update` методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Пытается сохранить все изменения в <xref:System.Data.DataTable> к базе данных. (Это включает удаление всех строк, удаленных из таблицы, добавление строки вставлены в таблицу и обновление строк в таблице, которые были изменены.)|  
|`TableAdapter.Update(DataSet)`|Несмотря на то, что он принимает набор данных, адаптер таблиц пытается сохранить все изменения в адаптере TableAdapter, связанного с <xref:System.Data.DataTable> к базе данных. (Это включает удаление всех строк, удаленных из таблицы, добавление строк, вставляемых в таблицу и обновление строк в таблице, которые были изменены.) **Примечание:** адаптера таблицы, связанного с <xref:System.Data.DataTable> является <xref:System.Data.DataTable> создается при первоначальной настройке адаптера.|  
|`TableAdapter.Update(DataRow)`|Пытается сохранить изменения в указанной строке <xref:System.Data.DataRow> к базе данных.|  
|`TableAdapter.Update(DataRows())`|Пытается сохранить изменения в любую строку в массив <xref:System.Data.DataRow>s в базу данных.|  
|`TableAdapter.Update("new column values", "original column values")`|Предпринимается попытка сохранить изменения в одной строке, который определяется параметром исходные значения столбца.|  
  
 Как правило, используется `TableAdapter.Update` метода, принимающего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, или <xref:System.Data.DataRow>(s), когда приложение использует наборы данных исключительно для хранения данных.  
  
 Как правило, используется `TableAdapter.Update` метод, который принимает значения столбцов, когда приложение использует объекты для хранения данных.  
  
 Если TableAdapter имеет `Update` метод, который принимает значения столбцов, то это означает, что либо TableAdapter настроен для использования хранимых процедур или его `GenerateDBDirectMethods` свойству `false`. Попробуйте задать TableAdapter `GenerateDBDirectMethods` свойства `true` изнутри [конструктор наборов данных](../data-tools/creating-and-editing-typed-datasets.md) и затем сохраните набор данных для повторного создания адаптера таблицы. Если TableAdapter по-прежнему имеет `Update` метод, который принимает значения столбцов, а затем таблицы, вероятно, не предоставляет достаточно сведений о схеме для различения отдельных строк (например, первичный ключ не имеет значение в таблице).  
  
## <a name="update-existing-records-using-tableadapters"></a>Обновить существующие записи, с помощью адаптеров таблиц  
 Адаптеры таблиц предоставляют различные способы обновления записей в базу данных в зависимости от требований приложения.  
  
 Если приложение использует наборы данных для хранения данных, то можно просто обновить записи в нужной <xref:System.Data.DataTable> , а затем вызвать `TableAdapter.Update` метод и передать либо <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, или массив <xref:System.Data.DataRow>s. В таблице выше описаны различные `Update` методы.  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>Для обновления записей в базе данных с помощью TableAdapter.Update-метод, принимающий DataSet, DataTable, DataRow или DataRows()  
  
1.  Изменение записей в нужной <xref:System.Data.DataTable> путем непосредственного редактирования <xref:System.Data.DataRow> в <xref:System.Data.DataTable>. Дополнительные сведения см. в разделе [как: изменение строк в таблице DataTable](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c).  
  
2.  После редактирования строк в <xref:System.Data.DataTable>, вызовите `TableAdapter.Update` метод. Можно управлять объемом данных для обновления путем передачи всего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, массив <xref:System.Data.DataRow>s или одной <xref:System.Data.DataRow>.  
  
     Ниже показано, как изменить запись в <xref:System.Data.DataTable> , а затем вызвать `TableAdapter.Update` метод, чтобы сохранить изменения в базу данных. (В этом примере используется таблица Region базы данных "Борей".)  
  
     [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
     [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
 Если приложение использует объекты для хранения данных в приложении, можно использовать TableAdapter `DBDirect` методы для отправки данных из объектов непосредственно к базе данных. Эти методы позволяют передавать отдельные значения для каждого столбца в качестве параметров метода. Вызов этого метода обновляет существующую запись в базе данных со значениями столбца, переданный методу.  
  
 В следующей процедуре используются базы данных Northwind `Region` таблицы в качестве примера.  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>Для обновления записей в базу данных с помощью TableAdapter.Update-метод, который принимает значения столбцов  
  
-   Вызов метода `Update` , передавая в новых и исходные значения для каждого столбца в качестве параметров.  
  
    > [!NOTE]
    >  Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>Обновление записей с помощью командных объектов  
 Следующий пример обновляет существующие записи непосредственно в базу данных с помощью объектов команд. Дополнительные сведения об использовании объектов command для выполнения команд и хранимых процедур см. в разделе [выборка данных в приложении](../data-tools/fetching-data-into-your-application.md).  
  
 В следующей процедуре используются базы данных Northwind `Region` таблицы в качестве примера.  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>Чтобы обновить существующие записи в базу данных с помощью командных объектов  
  
-   Создание объекта команды; Задайте его `Connection`, `CommandType`, и `CommandText` его свойства и затем открыть соединение и выполните команду.  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Необходимо иметь доступ для базы данных, которую вы пытаетесь подключиться, а также разрешение на обновление записей в нужную таблицу.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о TableAdapter](../data-tools/tableadapter-overview.md)   
 [Практическое: удаление записей в базе данных](../data-tools/how-to-delete-records-in-a-database.md)   
 [Вставка новых записей в базу данных](../data-tools/insert-new-records-into-a-database.md)   
 [Сохранение данных из объекта в базе данных](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Общие сведения о данных приложений в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)