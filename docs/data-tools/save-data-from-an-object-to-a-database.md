---
title: Сохранение данных из объекта в базе данных
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 42bbdb5cff0d244701e28730ab6b12d70b49a920
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="save-data-from-an-object-to-a-database"></a>Сохранение данных из объекта в базе данных
Можно сохранить данные в объектах в базе данных путем передачи значения из объекта в один из методов DBDirect адаптера таблицы (например, `TableAdapter.Insert`). Дополнительные сведения см. в разделе [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

 Чтобы сохранить данные из коллекции объектов, перебор коллекции объектов (например, для следующего цикла) и отправьте значения для каждого объекта базы данных с помощью одного из методов DBDirect адаптера таблицы.

 По умолчанию методы DBDirect создаются в TableAdapter, который может быть запущен непосредственно к базе данных. Эти методы могут вызываться напрямую и не требуют <xref:System.Data.DataSet> или <xref:System.Data.DataTable> объектов для согласования изменений для отправки обновлений в базу данных.

> [!NOTE]
>  При настройке адаптера таблицы, основной запрос должен предоставить достаточно данных для создания с помощью методов DBDirect. Например если он настроен для запроса данных из таблицы, у которого нет определен столбец первичного ключа, не создает DBDirect-методы.

|Метод DBDirect адаптера таблицы|Описание|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Добавление новых записей в базу данных и позволяет передавать значения отдельных столбцов в качестве параметров метода.|
|`TableAdapter.Update`|Обновляет существующие записи в базе данных. `Update` Метод принимает исходные и новые значения столбцов в качестве параметров метода. Исходные значения используются для обнаружения исходной записи, а новые значения используются для обновления этой записи.<br /><br /> `TableAdapter.Update` Метод также используется для согласования изменений в наборе данных обратно в базу данных, выполнив <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, или массив <xref:System.Data.DataRow>как параметры метода.|
|`TableAdapter.Delete`|Удаляет существующие записи из базы данных, основанный на исходных значениях столбцов, переданных в качестве параметров метода.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Для сохранения новых записей из объекта в базе данных

-   Создайте записи, передавая значения в `TableAdapter.Insert` метод.

     В следующем примере создается новая запись клиента в `Customers` таблицы путем передачи значений в `currentCustomer` объект `TableAdapter.Insert` метод.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Чтобы обновить существующие записи из объекта в базе данных

-   Измените записи путем вызова `TableAdapter.Update` метод, передав новые значения для обновления записи и исходных значений для поиска записи.

    > [!NOTE]
    >  Необходимо, чтобы сохранить исходные значения для передачи их в объект `Update` метод. В этом примере используются свойства с `orig` префикс для хранения исходных значений.

     Следующий пример обновляет существующую запись в `Customers` таблицы путем передачи новых и исходные значения в `Customer` объект `TableAdapter.Update` метод.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

### <a name="to-delete-existing-records-from-a-database"></a>Для удаления существующих записей из базы данных

-   Удалить записи путем вызова `TableAdapter.Delete` метода и передачи исходных значений для поиска записи.

    > [!NOTE]
    >  Необходимо, чтобы сохранить исходные значения для передачи их в объект `Delete` метод. В этом примере используются свойства с `orig` префикс для хранения исходных значений.

     Следующий пример удаляет запись из `Customers` таблицы путем передачи исходных значений в `Customer` объект `TableAdapter.Delete` метод.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>Безопасность платформы .NET Framework
 Необходимо иметь разрешение на выполнение инструкций INSERT, UPDATE или DELETE для таблицы в базе данных.

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)