---
title: Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 26bcab8d589c1fedcbbc4eb1f8b06bb1c04cac53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567026"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter

В дополнение к `InsertCommand`, `UpdateCommand`, и `DeleteCommand`, адаптеры таблиц создаются с помощью методов, которые могут выполняться непосредственно в базе данных. Эти методы можно вызывать (`TableAdapter.Insert`, `TableAdapter.Update`, и `TableAdapter.Delete`) для управления данными непосредственно в базе данных.

Если вы не хотите создавать эти прямые методы, задайте `GenerateDbDirectMethods` свойства `false` в **свойства** окна. Если все запросы будут добавлены в дополнение к основной запрос адаптера таблицы TableAdapter, они являются отдельными запросами, которые не создают эти `DbDirect` методы.

## <a name="send-commands-directly-to-a-database"></a>Отправлять команды непосредственно в базу данных

Вызов метода `DbDirect` метод, который выполняет задачу, вы пытались выполнить.

### <a name="to-insert-new-records-directly-into-a-database"></a>Для вставки новых записей непосредственно в базу данных

- Вызов метода `Insert` метод, передав значения для каждого столбца в качестве параметров. В следующей процедуре используется `Region` таблицы в базе данных "Борей" в качестве примера.

    > [!NOTE]
    > Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Для обновления записей непосредственно в базе данных

- Вызов метода `Update` , передавая в новых и исходные значения для каждого столбца в качестве параметров.

    > [!NOTE]
    > Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Для удаления записей непосредственно из базы данных

- Вызов метода `Delete` метод, передав значения для каждого столбца в качестве параметров `Delete` метод. В следующей процедуре используется `Region` таблицы в базе данных "Борей" в качестве примера.

    > [!NOTE]
    > Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>См. также

- [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)