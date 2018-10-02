---
title: 'Практическое: сохранение изменений набора данных в базе данных | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: dbab29afdfa5dc063e6785c00796f63efba9891b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569939"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>Практическое руководство. Сохранение изменений набора данных в базе данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После изменения и проверки данных в наборе данных может потребоваться отправки обновленных данных обратно в базу данных. Чтобы отправить измененные данные в базу данных, вызывается `Update` метод [TableAdapter](../data-tools/tableadapter-overview.md) или адаптер данных. Адаптера `Update` метод обновляет в одну таблицу данных и выполняет нужную команду (INSERT, UPDATE или DELETE), на основе <xref:System.Data.DataRow.RowState%2A> каждой строки данных в таблице.  
  
 При сохранении данных в связанных таблицах, Visual Studio предоставляет компонент TableAdapterManager, который помогает выполнять сохранение в нужном порядке на основе ограничений внешнего ключа, определенные в базе данных. Дополнительные сведения см. в разделе [иерархическое обновление Обзор](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Так как попытка обновления источника данных содержимое набора данных может привести к ошибкам, необходимо поместить код, который вызывает адаптера `Update` метод внутри `try` / `catch` блока.  
  
 Точная процедура для обновления источника данных может изменяться в зависимости от потребностей бизнеса, но приложение должно включать следующие этапы:  
  
1.  Выполнение кода, отправки обновлений в базу данных в пределах `try` / `catch` блока.  
  
2.  Если исключение перехватывается, найдите строку данных, которая вызвала ошибку. Дополнительные сведения см. в разделе [как: найти строки, имеют ошибки](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Устраните ошибку в данные строк (программным способом в том случае, если возможно, или с предоставлением недопустимую строку пользователю для изменения) и повторите попытку обновления (<xref:System.Data.DataRow.HasErrors%2A> свойство, <xref:System.Data.DataTable.GetErrors%2A> метод).  
  
## <a name="saving-data-to-a-database"></a>Сохранение данных в базе данных  
 Вызовите `Update` метод адаптера TableAdapter или данных, передав имя таблицы данных, которая содержит значения для записи в базу данных. Дополнительные сведения о сохранении данных из в одну таблицу данных в базу данных, см. в разделе [Пошаговое руководство: сохранение данных в базу данных (одна таблица)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>Обновление базы данных с набором данных с помощью адаптера таблицы  
  
-   Заключите `TableAdapter.Update` метод внутри `try` / `catch` блока. В следующем примере показано, как попытка обновления с содержимым `Customers` в таблицу `NorthwindDataSet`.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>Обновление базы данных с набором данных с помощью адаптера данных  
  
-   Заключите `DataAdapter.Update` метод внутри `try` / `catch` блока. В следующем примере показано, как попытка обновления к источнику данных с содержимым `Table1` в `DataSet1`.  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>Обновление двух связанных таблиц в наборе данных  
 При обновлении связанных таблиц в наборе данных, очень важно для обновления в правильной последовательности, чтобы уменьшить вероятность нарушения ограничений ссылочной целостности. Порядок выполнения команды также будет зависеть от индексов <xref:System.Data.DataRowCollection> в наборе данных. Чтобы предотвратить возникновение ошибок целостности данных, рекомендуется обновить базу данных в следующей последовательности:  
  
1.  Дочерняя таблица: удаление записей.  
  
2.  Родительская таблица: вставки, обновления и удаления записей.  
  
3.  Дочерняя таблица: вставляют и обновляют записи.  
  
 Подробные сведения о сохранении данных из нескольких таблиц см. в разделе [сохранение данных в базе данных (несколько таблиц)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
 При обновлении двух или более связанных таблиц следует включить всю логику обновления в рамках транзакции. Транзакция — это процесс, который подтверждает успешное внесение связанных изменений в базу данных перед фиксацией изменений. Дополнительные сведения см. [транзакции и параллельность](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>Для обновления двух связанных таблиц с помощью адаптера таблицы  
  
1.  Создайте три временных <xref:System.Data.DataTable>для хранения различных записей.  
  
2.  Вызовите `Update` метод для каждого подмножества строк изнутри `try` / `catch` блока. При возникновении ошибок обновления, предлагаемыми действиями — их разрешения.  
  
3.  Зафиксируйте изменения из набора данных в базу данных.  
  
4.  Удалите временные таблицы данных для освобождения ресурсов.  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>Для обновления двух связанных таблиц с помощью адаптера данных  
  
-   Вызовите `Update` метод каждого адаптера данных.  
  
     В следующем примере показано, как обновить источник данных с набором данных, содержащего связанные таблицы. Чтобы выполнить последовательность, приведенную выше три временных <xref:System.Data.DataTable>s должна быть создана для хранения различных записей. Затем `Update` метод будет вызываться для каждого подмножества строк изнутри `try` / `catch` блока. При возникновении ошибок обновления, предлагаемыми действиями — их разрешения. Завершает изменения в наборе данных. Наконец происходит удаление временных таблиц данных для освобождения ресурсов.  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>См. также  
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)