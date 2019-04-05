---
title: Обновление данных с помощью адаптера таблицы | Документация Майкрософт
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
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ec53e42a5e49d48e76c6c00e2ffbd5a8a3daafa0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992025"
---
# <a name="update-data-by-using-a-tableadapter"></a>Обновление данных с помощью адаптера таблицы TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
После изменения и проверки данных в наборе данных можно отправлять обновленные данные обратно в вызывающую databaseby `Update` метод адаптера таблицы. `Update` Метод обновляет в одну таблицу данных и выполняет нужную команду (INSERT, UPDATE или DELETE), на основе <xref:System.Data.DataRow.RowState%2A> каждой строки данных в таблице. Если набор данных имеет связанные таблицы, Visual Studio создает класс TableAdapterManager, которые можно использовать для выполнения обновлений. Класс TableAdapterManager гарантирует, что обновления выполняются в правильном порядке на основе ограничений внешнего ключа, которые определены в базе данных. При использовании элементов управления с привязкой данных, архитектура привязки данных создает переменную-член класса TableAdapterManager tableAdapterManager. Дополнительные сведения см. в разделе [иерархическое обновление Обзор](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  При попытке обновить источник данных с содержимым из набора данных, возможно возникновение ошибок. Чтобы избежать ошибок, мы рекомендуем thatyou поместите код, который вызывает адаптера `Update` метод внутри `try` / `catch` блока.  
  
 Точная процедура для обновления источника данных может изменяться в зависимости от потребностей бизнеса, но включает следующие шаги:  
  
1.  Вызовите адаптера `Update` метод в `try` / `catch` блока.  
  
2.  Если исключение перехватывается, найдите строку данных, которая вызвала ошибку. Дополнительные сведения см. в разделе [Как Найдите строки, содержащие ошибки](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Устраните ошибку в данные строк (программно или, предоставляя строку пользователю для изменения), а затем повторите попытку обновления (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="savedata-to-a-database"></a>SaveData в базе данных  
 Вызовите `Update` метод адаптера таблицы. Передайте имя таблицы данных, которая содержит значения для записи в базу данных.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Обновление базы данных с помощью адаптера таблицы  
  
-   Заключите TableAdapter`Update` метод в `try` / `catch` блока. В следующем примере показано, как обновить содержимое `Customers` в таблицу `NorthwindDataSet` изнутри `try` / `catch` блока.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
