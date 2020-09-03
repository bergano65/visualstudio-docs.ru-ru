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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 312bf75100d2b9b270b45776c5f7ded21ab6ac52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602336"
---
# <a name="update-data-by-using-a-tableadapter"></a>Обновление данных с помощью адаптера таблицы TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После изменения и проверки данных в наборе данных можно отправить обновленные данные обратно в датабасеби, вызвав `Update` метод адаптера таблицы. `Update`Метод обновляет одну таблицу данных и выполняет правильную команду (INSERT, UPDATE или DELETE) на основе <xref:System.Data.DataRow.RowState%2A> каждой строки данных в таблице. Когда набор данных содержит связанные таблицы, Visual Studio создает класс TableAdapterManager, который используется для обновления. Класс TableAdapterManager гарантирует, что обновления выполняются в правильном порядке на основе ограничений внешнего ключа, определенных в базе данных. При использовании привязанных к данным элементов управления архитектура привязки данных создает переменную-член класса TableAdapterManager, именуемую tableAdapterManager. Дополнительные сведения см. в разделе [Общие сведения о иерархическом обновлении](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).

> [!NOTE]
> При попытке обновить источник данных с помощью содержимого набора данных можно получить ошибки. Чтобы избежать ошибок, мы рекомендуем сатйоу разместить код, вызывающий метод адаптера, `Update` внутри `try` / `catch` блока.

 Точная процедура обновления источника данных может различаться в зависимости от бизнес-потребностей, но включает следующие шаги.

1. Вызовите метод адаптера `Update` в `try` / `catch` блоке.

2. Если исключение перехвачено, выберите строку данных, которая вызвала ошибку. Дополнительные сведения см. [в разделе инструкции. Обнаружение строк с ошибками](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).

3. Выверять проблему в строке данных (программным способом, если возможно, или путем представления недействительной строки пользователю для изменения), а затем повторите попытку обновления ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="savedata-to-a-database"></a>SaveData к базе данных
 Вызовите `Update` метод TableAdapter. Передайте имя таблицы данных, содержащей значения, записываемые в базу данных.

#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Обновление базы данных с помощью TableAdapter

- Заключите `Update` метод TableAdapter в `try` / `catch` блок. В следующем примере показано, как обновить содержимое `Customers` таблицы в `NorthwindDataSet` `try` / `catch` блоке.

     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]

## <a name="see-also"></a>См. также:
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
