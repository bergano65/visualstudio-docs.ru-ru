---
title: "Практическое руководство. Сохранение данных из объекта в базе данных | Microsoft Docs"
ms.custom: ""
ms.date: "09/22/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "данные [Visual Studio], сохранение"
  - "доступ к данным [Visual Studio], объекты"
  - "сохранение данных"
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Сохранение данных из объекта в базе данных
Можно сохранить данные объектов в базу данных путем передачи значений из объекта в один из методов DBDirect адаптера таблицы \(например `TableAdapter.Insert`\).  Дополнительные сведения см. в разделе [Общие сведения об адаптере таблиц](../data-tools/tableadapter-overview.md).  
  
 Чтобы сохранить данные из коллекции объектов, просмотрите всю коллекцию объектов \(например циклом for\-next\) и отправьте значения каждого объекта в базу данных с помощью одного из методов DBDirect адаптера таблиц.  
  
 По умолчанию методы DBDirect создаются для адаптера таблиц, который может работать непосредственно с базой данных.  Эти методы можно вызывать напрямую. Для отправки обновлений к базе данных они не требуют объектов <xref:System.Data.DataSet> или <xref:System.Data.DataTable> для согласования изменений.  
  
> [!NOTE]
>  При настройке адаптера таблиц в главном запросе необходимо указать достаточно сведений для создания методов DBDirect.  Например, если адаптер таблиц настроен для таблицы, у которой не определен столбец первичного ключа, он не формирует DBDirect\-методов.  
  
|Метод DBDirect адаптера таблиц|Описание|  
|------------------------------------|--------------|  
|`TableAdapter.Insert`|Добавляет новые записи в базу данных, позволяя передать отдельные значения столбцов в качестве параметров метода.|  
|`TableAdapter.Update`|Обновляет в базе данных существующие записи.  Метод `Update` принимает исходные и новые значения столбцов в качестве параметров метода.  Исходные значения используются для обнаружения исходной записи, а новые значения используются для обновления этой записи.<br /><br /> Метод `TableAdapter.Update` также используется для согласования изменений в наборе данных с базой данных путем принятия в качестве параметров метода <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> или массива <xref:System.Data.DataRow>.|  
|`TableAdapter.Delete`|Удаляет существующие записи из базы данных на основе исходных значений столбца, переданных как параметры метода.|  
  
### Для сохранения новых записей из объекта в базу данных:  
  
-   Создайте записи, передавая значения в метод `TableAdapter.Insert`.  
  
     В следующем примере создается новая запись клиента в таблице `Customers` путем передачи значений в объекте `currentCustomer` методу `TableAdapter.Insert`.  
  
     [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### Чтобы обновить существующие записи из объекта в базу данных:  
  
-   Измените записи путем вызова метода `TableAdapter.Update` и передачи новых значений для обновления записи и исходных значений для поиска записи.  
  
    > [!NOTE]
    >  Объекту необходимо сохранить исходные значения для передачи их методу `Update`.  В этом примере для хранения исходных значений используются свойства с префиксом `orig`.  
  
     В следующем примере обновляется существующая запись в таблице `Customers` путем передачи новых и исходных значений в объекте `Customer` методу `TableAdapter.Update`.  
  
     [!code-cs[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### Для удаления существующих записей из базы данных:  
  
-   Удалить записи можно, передав исходные значения для поиска записи методу `TableAdapter.Delete`.  
  
    > [!NOTE]
    >  Объекту необходимо сохранить исходные значения для передачи их методу `Delete`.  В этом примере для хранения исходных значений используются свойства с префиксом `orig`.  
  
     В следующем примере удаляется запись из таблицы `Customers` путем передачи исходных значений в объекте `Customer` в метод `TableAdapter.Delete`.  
  
     [!code-cs[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## Безопасность платформы .NET Framework  
 Для выполнения инструкций INSERT, UPDATE или DELETE над таблицами в базе данных необходимо иметь разрешения.  
  
## См. также  
 [Привязка объектов в Visual Studio](../data-tools/bind-objects-in-visual-studio.md)   
 [Практическое руководство. Подключение к данным в объектах](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [Пошаговое руководство. Подключение к данным в объектах \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [Практическое руководство. Непосредственный доступ к базе данных с помощью адаптера таблицы](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Сохранение данных](../data-tools/saving-data.md)