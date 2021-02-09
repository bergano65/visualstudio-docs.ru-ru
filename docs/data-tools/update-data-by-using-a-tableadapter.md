---
title: Обновление данных с помощью адаптера таблицы TableAdapter
description: Обновление данных в наборе данных. Отправьте данные обратно в базу данных, вызвав метод Update объекта TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 5d03a6dbe728d77fb9158ec02e1f59016e7c4a99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858284"
---
# <a name="update-data-by-using-a-tableadapter"></a>Обновление данных с помощью адаптера таблицы TableAdapter

После изменения и проверки данных в наборе данных можно отправить обновленные данные обратно в базу данных, вызвав `Update` метод [TableAdapter](../data-tools/create-and-configure-tableadapters.md). `Update`Метод обновляет одну таблицу данных и выполняет правильную команду (INSERT, UPDATE или DELETE) на основе <xref:System.Data.DataRow.RowState%2A> каждой строки данных в таблице. Когда набор данных содержит связанные таблицы, Visual Studio создает класс TableAdapterManager, который используется для обновления. Класс TableAdapterManager гарантирует, что обновления выполняются в правильном порядке на основе ограничений внешнего ключа, определенных в базе данных. При использовании привязанных к данным элементов управления архитектура привязки данных создает переменную-член класса TableAdapterManager, именуемую tableAdapterManager.

> [!NOTE]
> При попытке обновить источник данных с помощью содержимого набора данных можно получить ошибки. Чтобы избежать ошибок, рекомендуется разместить код, вызывающий метод адаптера, `Update` внутри `try` / `catch` блока.

Точная процедура обновления источника данных может различаться в зависимости от бизнес-потребностей, но включает следующие шаги.

1. Вызовите метод адаптера `Update` в `try` / `catch` блоке.

2. Если исключение перехвачено, выберите строку данных, которая вызвала ошибку.

3. Выверять проблему в строке данных (программным способом, если возможно, или путем представления недействительной строки пользователю для изменения), а затем повторите попытку обновления ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="save-data-to-a-database"></a>Сохранение данных в базе данных

Вызовите `Update` метод TableAdapter. Передайте имя таблицы данных, содержащей значения, записываемые в базу данных.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Обновление базы данных с помощью TableAdapter

- Заключите `Update` метод TableAdapter в `try` / `catch` блок. В следующем примере показано, как обновить содержимое `Customers` таблицы в `NorthwindDataSet` `try` / `catch` блоке.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>См. также раздел

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
