---
title: Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 22d84e9b4beafd64cc629a295bcfa7f9f67afb6d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282570"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter

В дополнение к классам `InsertCommand` , `UpdateCommand` и `DeleteCommand` адаптеры таблиц создаются с помощью методов, которые могут выполняться непосредственно в базе данных. Эти методы ( `TableAdapter.Insert` , `TableAdapter.Update` и) можно вызывать `TableAdapter.Delete` для управления данными непосредственно в базе данных.

Если вы не хотите создавать эти прямые методы, задайте для свойства TableAdapter значение `GenerateDbDirectMethods` `false` в окне **Свойства** . Если какие-либо запросы добавляются в TableAdapter в дополнение к основному запросу TableAdapter, они являются автономными запросами, которые не создают эти `DbDirect` методы.

## <a name="send-commands-directly-to-a-database"></a>Отправка команд непосредственно в базу данных

Вызовите `DbDirect` метод TableAdapter, который выполняет задачу, которую вы пытаетесь выполнить.

### <a name="to-insert-new-records-directly-into-a-database"></a>Вставка новых записей непосредственно в базу данных

- Вызовите метод TableAdapter `Insert` , передав значения для каждого столбца в качестве параметров. В следующей процедуре в `Region` качестве примера используется таблица в базе данных Northwind.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Обновление записей непосредственно в базе данных

- Вызовите метод TableAdapter `Update` , передав новые и исходные значения для каждого столбца в качестве параметров.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Удаление записей непосредственно из базы данных

- Вызовите метод TableAdapter `Delete` , передав значения для каждого столбца в качестве параметров `Delete` метода. В следующей процедуре в `Region` качестве примера используется таблица в базе данных Northwind.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>См. также

- [Заполнение наборов данных с помощью адаптеров таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)
