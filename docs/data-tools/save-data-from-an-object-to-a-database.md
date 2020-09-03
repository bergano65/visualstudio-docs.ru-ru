---
title: Сохранение данных из объекта в базе данных
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4afa0d376366b154501e1a0e4488af57b4448a32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281660"
---
# <a name="save-data-from-an-object-to-a-database"></a>Сохранение данных из объекта в базе данных

Можно сохранить данные в объектах в базе данных, передав значения из объекта в один из методов DBDirect адаптера таблицы (например, `TableAdapter.Insert` ). Дополнительные сведения см. в разделе [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Чтобы сохранить данные из коллекции объектов, пройдите через коллекцию объектов (например, цикл For-Next) и отправьте значения для каждого объекта в базу данных с помощью одного из `DBDirect` методов TableAdapter.

По умолчанию `DBDirect` методы создаются на TableAdapter, который может выполняться непосредственно в базе данных. Эти методы можно вызывать напрямую, не требуя <xref:System.Data.DataSet> , <xref:System.Data.DataTable> чтобы объекты или могли согласовать изменения для отправки обновлений в базу данных.

> [!NOTE]
> При настройке TableAdapter основной запрос должен предоставить достаточно информации для `DBDirect` создаваемых методов. Например, если адаптер таблицы настроен для запроса данных из таблицы, для которой не определен первичный ключевой столбец, то методы не создаются `DBDirect` .

|Метод TableAdapter DBDirect|Описание|
| - |-----------------|
|`TableAdapter.Insert`|Добавляет новые записи в базу данных и позволяет передавать отдельные значения столбцов в качестве параметров метода.|
|`TableAdapter.Update`|Обновляет существующие записи в базе данных. `Update`Метод принимает исходные и новые значения столбцов в качестве параметров метода. Исходные значения используются для нахождение исходной записи, а для обновления этой записи используются новые значения.<br /><br /> `TableAdapter.Update`Метод также используется для согласования изменений в наборе данных с базой данных с помощью <xref:System.Data.DataSet> ,, <xref:System.Data.DataTable> <xref:System.Data.DataRow> или массива <xref:System.Data.DataRow> s в качестве параметров метода.|
|`TableAdapter.Delete`|Удаляет существующие записи из базы данных на основе значений исходных столбцов, переданных в качестве параметров метода.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Сохранение новых записей из объекта в базу данных

- Создайте записи, передав значения в `TableAdapter.Insert` метод.

     В следующем примере создается новая запись клиента в `Customers` таблице путем передачи значений в `currentCustomer` объект в `TableAdapter.Insert` метод.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Обновление существующих записей из объекта в базу данных

- Измените записи, вызвав `TableAdapter.Update` метод, передав новые значения для обновления записи и передав исходные значения для нахождения записи.

    > [!NOTE]
    > Объекту необходимо сохранить исходные значения, чтобы передать их в `Update` метод. В этом примере используются свойства с `orig` префиксом для хранения исходных значений.

     В следующем примере существующая запись в таблице обновляется `Customers` путем передачи новых и исходных значений в `Customer` объект в `TableAdapter.Update` метод.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Удаление существующих записей из базы данных

- Удалите записи, вызвав `TableAdapter.Delete` метод и передав исходные значения для нахождения записи.

    > [!NOTE]
    > Объекту необходимо сохранить исходные значения, чтобы передать их в `Delete` метод. В этом примере используются свойства с `orig` префиксом для хранения исходных значений.

     В следующем примере удаляется запись из `Customers` таблицы путем передачи исходных значений в `Customer` объект в `TableAdapter.Delete` метод.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>Безопасность в .NET

Необходимо иметь разрешение на выполнение выбранного `INSERT` , `UPDATE` или `DELETE` для таблицы в базе данных.

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
