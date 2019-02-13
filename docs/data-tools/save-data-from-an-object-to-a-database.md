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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5e7762b50d486f50ed59f489ef45641908d61612
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933110"
---
# <a name="save-data-from-an-object-to-a-database"></a>Сохранение данных из объекта в базе данных

Можно сохранить данные в объекты в базе данных путем передачи значения из объекта в один из методов DBDirect адаптера таблицы (например, `TableAdapter.Insert`). Дополнительные сведения см. в разделе [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Для сохранения данных из коллекции объектов, циклический перебор коллекции объектов (например, для следующего цикла) и отправки значений для каждого объекта в базу данных с помощью одного из TableAdapter `DBDirect` методы.

По умолчанию `DBDirect` методы создаются на TableAdapter, который может быть запущен непосредственно в базе данных. Эти методы можно вызывать напрямую и не требуют <xref:System.Data.DataSet> или <xref:System.Data.DataTable> объектов для согласования изменений для отправки обновлений в базу данных.

> [!NOTE]
> При настройке адаптера таблицы, основного запроса должно содержать достаточно информации для `DBDirect` создания методов. Например, если он настроен для запроса данных из таблицы, не является первичным ключевым столбцом, не вызывает `DBDirect` методы.

|Метод TableAdapter DBDirect|Описание|
| - |-----------------|
|`TableAdapter.Insert`|Добавляет новые записи в базу данных и позволяет передавать значения отдельных столбцов в качестве параметров метода.|
|`TableAdapter.Update`|Обновляет существующие записи в базе данных. `Update` Метод принимает исходные и новые значения столбцов как параметры метода. Исходные значения используются для обнаружения исходной записи, а новые значения используются для обновления этой записи.<br /><br /> `TableAdapter.Update` Метод также используется для согласования изменений в наборе данных в базе данных, используя <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, или массив <xref:System.Data.DataRow>s как параметры метода.|
|`TableAdapter.Delete`|Удаляет существующие записи из базы данных, основанный на исходных значениях столбца, переданный в качестве параметров метода.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Для сохранения новых записей из объекта в базе данных

-   Создайте записи путем передачи значения `TableAdapter.Insert` метод.

     В следующем примере создается новая запись клиента в `Customers` таблицы, передав значения в `currentCustomer` объект `TableAdapter.Insert` метод.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Чтобы обновить существующие записи из объекта в базе данных

-   Изменить записи путем вызова `TableAdapter.Update` метод, передав новые значения для обновления записи и передачи в исходные значения для поиска записи.

    > [!NOTE]
    > Необходимо, чтобы сохранить исходные значения для передачи их в объект `Update` метод. В этом примере используются свойства с `orig` префикс для хранения оригинальных значений.

     Следующий пример обновляет существующую запись в `Customers` таблицы путем передачи новых и исходные значения в `Customer` объект `TableAdapter.Update` метод.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Для удаления существующих записей из базы данных

-   Удалить записи путем вызова `TableAdapter.Delete` и передав исходные значения для поиска записи.

    > [!NOTE]
    > Необходимо, чтобы сохранить исходные значения для передачи их в объект `Delete` метод. В этом примере используются свойства с `orig` префикс для хранения оригинальных значений.

     Следующий пример удаляет запись из `Customers` таблицы, передав исходные значения в `Customer` объект `TableAdapter.Delete` метод.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>безопасность платформы .NET Framework

Необходимо иметь разрешение на выполнение выбранного `INSERT`, `UPDATE`, или `DELETE` для таблицы в базе данных.

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)