---
title: Обновление данных с помощью адаптера таблицы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c5188f56e440f7ec00f7537602aff10723441c3a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="update-data-by-using-a-tableadapter"></a>Обновление данных с помощью адаптера таблицы
После изменения и проверки данных в наборе данных отправки обновленных данных обратно в базу данных, вызвав `Update` метод [TableAdapter](../data-tools/create-and-configure-tableadapters.md). `Update` Метод обновляет одну таблицу с данными и запускает нужную команду (INSERT, UPDATE или DELETE), на основе <xref:System.Data.DataRow.RowState%2A> каждой строки данных в таблице. Если набор данных имеет связанные таблицы, Visual Studio создает TableAdapterManager класс, который можно использовать для выполнения обновлений. Класс TableAdapterManager гарантирует, что обновления выполняются в правильном порядке, в зависимости от ограничений внешнего ключа, определенных в базе данных. При использовании элементов управления с привязкой к данным, архитектура привязки данных создает переменную-член класса TableAdapterManager вызывается tableAdapterManager. 
  
> [!NOTE]
>  При попытке обновления источника данных содержимым набора данных, возможно возникновение ошибок. Чтобы избежать ошибок, рекомендуется поместить код, который вызывает адаптера `Update` метод внутри `try` / `catch` блока.  
  
 Точные процедуры для обновления источника данных может изменяться в зависимости от потребностей бизнеса, но включает следующие шаги:  
  
1.  Вызовите адаптера `Update` метод в `try` / `catch` блока.  
  
2.  Если исключение перехватывается, найдите строку данных, которая вызвала ошибку. 
  
3.  Устраните ошибку в данные строк (программно или с предоставлением пользователю для изменения Недопустимая строка), а затем повторите попытку обновления (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="save-data-to-a-database"></a>Сохранение данных в базе данных  
 Вызовите `Update` метод адаптера таблицы. Передайте имя таблицы данных, которая содержит значения для записи в базу данных.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Обновление базы данных с помощью адаптера таблицы  
  
-   Заключите его`Update` метод в `try` / `catch` блока. В следующем примере показано, как обновить содержимое `Customers` в таблицу `NorthwindDataSet` изнутри `try` / `catch` блока.  
  
     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)