---
title: Сохранение данных из объекта в базе данных | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: acbbf9f309573f110da3b7dd0a53ede36150a319
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207458"
---
# <a name="save-data-from-an-object-to-a-database"></a>Сохранение данных из объекта в базе данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Можно сохранить данные в объекты в базе данных путем передачи значения из объекта в один из методов DBDirect адаптера таблицы (например, `TableAdapter.Insert`). Для получения дополнительной информации см. [TableAdapter Overview](../data-tools/tableadapter-overview.md).  
  
 Для сохранения данных из коллекции объектов, циклический перебор коллекции объектов (например, для следующего цикла) и отправки значений для каждого объекта в базу данных с помощью одного из методов DBDirect адаптера таблицы.  
  
 По умолчанию методы DBDirect создаются в TableAdapter, который может быть запущен непосредственно в базе данных. Эти методы можно вызывать напрямую и не требуют <xref:System.Data.DataSet> или <xref:System.Data.DataTable> объектов для согласования изменений для отправки обновлений в базу данных.  
  
> [!NOTE]
>  При настройке адаптера таблицы, основного запроса должен содержать достаточно информации для создания с помощью методов DBDirect. Например если он настроен для запроса данных из таблицы, не является первичным ключевым столбцом, не создает DBDirect-методы.  
  
|Метод DBDirect адаптера таблицы|Описание|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Добавляет новые записи в базу данных и позволяет передавать значения отдельных столбцов в качестве параметров метода.|  
|`TableAdapter.Update`|Обновляет существующие записи в базе данных. `Update` Метод принимает исходные и новые значения столбцов как параметры метода. Исходные значения используются для обнаружения исходной записи, а новые значения используются для обновления этой записи.<br /><br /> `TableAdapter.Update` Метод также используется для согласования изменений в наборе данных в базе данных, используя <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, или массив <xref:System.Data.DataRow>s как параметры метода.|  
|`TableAdapter.Delete`|Удаляет существующие записи из базы данных, основанный на исходных значениях столбца, переданный в качестве параметров метода.|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>Для сохранения новых записей из объекта в базе данных  
  
-   Создайте записи путем передачи значения `TableAdapter.Insert` метод.  
  
     В следующем примере создается новая запись клиента в `Customers` таблицы, передав значения в `currentCustomer` объект `TableAdapter.Insert` метод.  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Чтобы обновить существующие записи из объекта в базе данных  
  
-   Изменить записи путем вызова `TableAdapter.Update` метод, передав новые значения для обновления записи и передачи в исходные значения для поиска записи.  
  
    > [!NOTE]
    >  Необходимо, чтобы сохранить исходные значения для передачи их в объект `Update` метод. В этом примере используются свойства с `orig` префикс для хранения оригинальных значений.  
  
     Следующий пример обновляет существующую запись в `Customers` таблицы путем передачи новых и исходные значения в `Customer` объект `TableAdapter.Update` метод.  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>Для удаления существующих записей из базы данных  
  
-   Удалить записи путем вызова `TableAdapter.Delete` и передав исходные значения для поиска записи.  
  
    > [!NOTE]
    >  Необходимо, чтобы сохранить исходные значения для передачи их в объект `Delete` метод. В этом примере используются свойства с `orig` префикс для хранения оригинальных значений.  
  
     Следующий пример удаляет запись из `Customers` таблицы, передав исходные значения в `Customer` объект `TableAdapter.Delete` метод.  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Необходимо иметь разрешение на выполнение инструкций INSERT, UPDATE или DELETE для таблицы в базе данных.  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)

