---
title: Прямой доступ к базе данных с помощью адаптера таблицы
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
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b1a3b35cc491ed91e07316444c31cf4a29ef1517
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Прямой доступ к базе данных с помощью адаптера таблицы
В дополнение к `InsertCommand`, `UpdateCommand`, и `DeleteCommand`, адаптеры таблиц создаются с помощью методов, которые могут быть запущены напрямую с базой данных. Эти методы (`TableAdapter.Insert`, `TableAdapter.Update`, и `TableAdapter.Delete`) может быть вызван для работы с данными непосредственно в базе данных.

 Если вы не хотите создавать эти непосредственные методы, задайте `GenerateDbDirectMethods` свойства `false` в **свойства** окна. Если помимо основного запроса адаптера таблицы TableAdapter будут добавлены все запросы, они являются отдельными запросами, не создают эти методы DbDirect.

## <a name="send-commands-directly-to-a-database"></a>Отправлять команды в базу данных
 Вызовите метод DbDirect адаптера таблицы, который выполняет задачу, которую вы пытаетесь выполнить.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Для вставки новых записей непосредственно в базу данных

-   Вызов метода `Insert` метод, передав значения для каждого столбца в качестве параметров. В следующей процедуре используется `Region` таблицы в базе данных "Борей" в качестве примера.

    > [!NOTE]
    >  Если экземпляра нет, создайте экземпляр адаптера таблицы, который вы хотите использовать.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

#### <a name="to-update-records-directly-in-a-database"></a>Чтобы обновить записи непосредственно в базе данных

-   Вызов метода `Update` метод, передав новые и оригинальные значения для каждого столбца в качестве параметров.

    > [!NOTE]
    >  Если экземпляра нет, создайте экземпляр адаптера таблицы, который вы хотите использовать.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

#### <a name="to-delete-records-directly-from-a-database"></a>Для удаления записей непосредственно из базы данных

-   Вызов метода `Delete` метод, передав значения для каждого столбца в качестве параметров `Delete` метод. В следующей процедуре используется `Region` таблицы в базе данных "Борей" в качестве примера.

    > [!NOTE]
    >  Если экземпляра нет, создайте экземпляр адаптера таблицы, который вы хотите использовать.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>См. также

- [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)