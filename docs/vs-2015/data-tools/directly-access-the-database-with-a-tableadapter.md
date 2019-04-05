---
title: Прямой доступ к базе данных с помощью адаптера таблицы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 372985c0878abbcfd42eab795cf8e2372bf65dd7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980810"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Непосредственный доступ к базе данных с помощью адаптера таблицы TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
В дополнение к `InsertCommand`, `UpdateCommand`, и `DeleteCommand`, адаптеры таблиц создаются с помощью методов, которые могут выполняться непосредственно в базе данных. Эти методы (`TableAdapter.Insert`, `TableAdapter.Update`, и `TableAdapter.Delete`) можно вызывать для управления данными непосредственно в базе данных.  
  
 Если вы не хотите создавать эти прямые методы, задайте `GenerateDbDirectMethods` свойства `false` в **свойства** окна. Если все запросы будут добавлены в дополнение к основной запрос адаптера таблицы TableAdapter, они являются отдельными запросами, которые не создают эти методы DbDirect.  
  
## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly в базе данных  
 Вызовите метод DbDirect адаптера таблицы, который выполняет задачу, которую вы пытаетесь выполнить.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Для вставки новых записей непосредственно в базу данных  
  
-   Вызов метода `Insert` метод, передав значения для каждого столбца в качестве параметров. В следующей процедуре используется `Region` таблицы Northwind databaseas пример.  
  
    > [!NOTE]
    >  Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Для обновления записей непосредственно в базе данных  
  
-   Вызов метода `Update` , передавая в новых и исходные значения для каждого столбца в качестве параметров.  
  
    > [!NOTE]
    >  Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Для удаления записей непосредственно из базы данных  
  
-   Вызов метода `Delete` метод, передав значения для каждого столбца в качестве параметров `Delete` метод. В следующей процедуре используется `Region` таблицы Northwind databaseas пример.  
  
    > [!NOTE]
    >  Если у вас нет экземпляра, создайте экземпляр TableAdapter, который вы хотите использовать.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>См. также  
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)
