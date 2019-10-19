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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e8d5d8e3091b464084df065bb7b889db9fc2194f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648517"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter

Кроме `InsertCommand`, `UpdateCommand` и `DeleteCommand`, адаптеры таблиц создаются с помощью методов, которые могут выполняться непосредственно в базе данных. Эти методы (`TableAdapter.Insert`, `TableAdapter.Update` и `TableAdapter.Delete`) можно вызывать для управления данными непосредственно в базе данных.

Если вы не хотите создавать эти прямые методы, задайте для свойства `GenerateDbDirectMethods` TableAdapter значение `false` в окне **Свойства** . Если какие-либо запросы добавляются в TableAdapter в дополнение к основному запросу TableAdapter, они являются автономными запросами, которые не создают эти `DbDirect` методов.

## <a name="send-commands-directly-to-a-database"></a>Отправка команд непосредственно в базу данных

Вызовите метод `DbDirect` TableAdapter, который выполняет задачу, которую вы пытаетесь выполнить.

### <a name="to-insert-new-records-directly-into-a-database"></a>Вставка новых записей непосредственно в базу данных

- Вызовите метод `Insert` TableAdapter, передав значения для каждого столбца в качестве параметров. В следующей процедуре в качестве примера используется таблица `Region` в базе данных Northwind.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Обновление записей непосредственно в базе данных

- Вызовите метод `Update` TableAdapter, передав новые и исходные значения для каждого столбца в качестве параметров.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Удаление записей непосредственно из базы данных

- Вызовите метод `Delete` TableAdapter, передав значения для каждого столбца в качестве параметров метода `Delete`. В следующей процедуре в качестве примера используется таблица `Region` в базе данных Northwind.

    > [!NOTE]
    > Если у вас нет доступного экземпляра, создайте экземпляр TableAdapter, который нужно использовать.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>См. также

- [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)