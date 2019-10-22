---
title: Сохранение данных из объекта в базу данных | Документация Майкрософт
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
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c1470c831177e74e7670d696b44fc2b0119a9a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607459"
---
# <a name="save-data-from-an-object-to-a-database"></a>Сохранение данных из объекта в базе данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно сохранить данные в объектах в базе данных, передав значения из объекта в один из методов DBDirect адаптера таблицы (например, `TableAdapter.Insert`).

 Чтобы сохранить данные из коллекции объектов, пройдите через коллекцию объектов (например, цикл For-Next) и отправьте значения для каждого объекта в базу данных с помощью одного из методов DBDirect адаптера таблицы TableAdapter.

 По умолчанию методы DBDirect создаются в TableAdapter, который может выполняться непосредственно в базе данных. Эти методы можно вызывать напрямую и не требовать <xref:System.Data.DataSet> или <xref:System.Data.DataTable> объектов для согласования изменений для отправки обновлений в базу данных.

> [!NOTE]
> При настройке TableAdapter основной запрос должен предоставить достаточно информации для создания методов DBDirect. Например, если адаптер таблицы настроен для запроса данных из таблицы, для которой не определен первичный ключевой столбец, то методы DBDirect не создаются.

|Метод TableAdapter DBDirect|Описание|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Добавляет новые записи в базу данных и позволяет передавать отдельные значения столбцов в качестве параметров метода.|
|`TableAdapter.Update`|Обновляет существующие записи в базе данных. Метод `Update` принимает исходные и новые значения столбцов в качестве параметров метода. Исходные значения используются для нахождение исходной записи, а для обновления этой записи используются новые значения.<br /><br /> Метод `TableAdapter.Update` также используется для согласования изменений в наборе данных с базой данных путем создания <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> или массива <xref:System.Data.DataRow>s в качестве параметров метода.|
|`TableAdapter.Delete`|Удаляет существующие записи из базы данных на основе значений исходных столбцов, переданных в качестве параметров метода.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Сохранение новых записей из объекта в базу данных

- Создайте записи, передав значения в метод `TableAdapter.Insert`.

     В следующем примере создается новая запись клиента в `Customers` таблице путем передачи значений в объект `currentCustomer` в метод `TableAdapter.Insert`.

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Обновление существующих записей из объекта в базу данных

- Измените записи, вызвав метод `TableAdapter.Update`, передав новые значения для обновления записи и передав исходные значения для нахождения записи.

    > [!NOTE]
    > Объекту необходимо сохранить исходные значения, чтобы передать их в метод `Update`. В этом примере используются свойства с префиксом `orig` для хранения исходных значений.

     В следующем примере существующая запись обновляется в `Customers` таблице путем передачи новых и исходных значений в объект `Customer` в метод `TableAdapter.Update`.

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>Удаление существующих записей из базы данных

- Удалите записи, вызвав метод `TableAdapter.Delete` и передав исходные значения для нахождения записи.

    > [!NOTE]
    > Объекту необходимо сохранить исходные значения, чтобы передать их в метод `Delete`. В этом примере используются свойства с префиксом `orig` для хранения исходных значений.

     В следующем примере удаляется запись из таблицы `Customers` путем передачи исходных значений из объекта `Customer` в метод `TableAdapter.Delete`.

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>Безопасность платформы .NET Framework
 Необходимо иметь разрешение на выполнение выбранных операций вставки, обновления или удаления для таблицы в базе данных.

## <a name="see-also"></a>См. также раздел
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
