---
title: "Прямой доступ к базе данных с помощью адаптера таблицы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: bd8a4c54ba67af567e28e27e5d70d3576645f496
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)