---
title: "Практическое руководство. Обновление записей в базе данных | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "базы данных, обновление"
  - "записи, редактирование"
  - "записи, обновление"
  - "TableAdapter.Update - метод"
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Практическое руководство. Обновление записей в базе данных
Можно использовать метод `TableAdapter.Update` для обновления \(изменения\) записей в базе данных.  Метод `TableAdapter.Update` предоставляет несколько перегруженных версий, которые выполняют различные операции в зависимости от передаваемых параметров.  Важно понимать результаты вызова различных сигнатур метода.  
  
> [!NOTE]
>  Если приложение не использует адаптеры таблиц, можно использовать командные объекты для обновления записей в базе данных \(например, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  Дополнительные сведения по обновлению данных с помощью командных объектов содержатся в разделе "Обновление записей с помощью командных объектов" ниже.  
  
 В следующей таблице описывается поведение различных методов `TableAdapter.Update`:  
  
|Метод|Описание|  
|-----------|--------------|  
|`TableAdapter.Update(DataTable)`|Пытается сохранить все изменения <xref:System.Data.DataTable> в базе данных.  \(Это включает удаление всех строк, удаленных из таблицы, добавление вставленных в таблицу строк и обновление всех строк в таблице, которые были изменены.\)|  
|`TableAdapter.Update(DataSet)`|Хотя параметр принимает набор данных, адаптер таблиц пытается сохранить все изменения в связанной с ним таблице <xref:System.Data.DataTable> в базе данных.  \(Это включает удаление всех строк, удаленных из таблицы, добавление вставленных в таблицу строк и обновление всех строк в таблице, которые были изменены.\) **Note:**  Связанная с адаптером таблиц таблица <xref:System.Data.DataTable> является таблицей <xref:System.Data.DataTable>, созданной при первоначальной настройке TableAdapter.|  
|`TableAdapter.Update(DataRow)`|Пытается сохранить все изменения в указанной строке <xref:System.Data.DataRow> в базе данных.|  
|`TableAdapter.Update(DataRows())`|Пытается сохранить изменения в любой строке массива <xref:System.Data.DataRow> в базе данных.|  
|`TableAdapter.Update("new column values", "original column values")`|Пытается сохранить изменения в одной строке, определяемой исходными значениями столбцов.|  
  
 Как правило, используется метод `TableAdapter.Update`, который принимает <xref:System.Data.DataSet>, <xref:System.Data.DataTable> или <xref:System.Data.DataRow>, когда приложение использует наборы данных исключительно для хранения данных.  
  
 Как правило, используется метод `TableAdapter.Update`, который принимает значения столбцов, когда приложение использует объекты для хранения данных.  
  
 Если TableAdapter не имеет метода `Update`, который принимает значения столбцов, это означает, что либо TableAdapter настроен на использование сохраненных процедур, либо значение его свойства `GenerateDBDirectMethods` равно `false`.  Попробуйте присвоить свойству `GenerateDBDirectMethods` адаптера таблиц TableAdapter значение `true` из [Конструктора наборов данных](../data-tools/creating-and-editing-typed-datasets.md) и затем сохранить набор данных, чтобы заново создать адаптер таблиц.  Если TableAdapter по\-прежнему не имеет метода `Update`, который принимает значения столбцов, то таблица, скорее всего, не предоставляет достаточно сведений схемы для различения отдельных строк \(например, нет первичного ключа на таблице\).  
  
## Обновление существующих записей с помощью TableAdapter  
 TableAdapter предоставляет различные способы обновления записей в базе данных в зависимости от требований приложения.  
  
 Если приложение использует для хранения данных набор данных, можно просто обновить записи в нужной таблице <xref:System.Data.DataTable>, вызвать метод `TableAdapter.Update` и передать либо <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, либо массив <xref:System.Data.DataRow>.  В таблице выше описаны различные методы `Update`.  
  
#### Для обновления записей в базе данных с помощью метода TableAdapter.Update, принимающего объект DataSet, DataTable, DataRow или DataRows\(\):  
  
1.  Измените записи в нужной <xref:System.Data.DataTable> путем прямого редактирования <xref:System.Data.DataRow> в <xref:System.Data.DataTable>.  Дополнительные сведения см. в разделе [Практическое руководство. Редактирование строк в объекте DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).  
  
2.  После редактирования строк в <xref:System.Data.DataTable> вызовите метод `TableAdapter.Update`.  Можно контролировать объем данных для обновления путем передачи всего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, массива <xref:System.Data.DataRow> или одной <xref:System.Data.DataRow>.  
  
     Следующий фрагмент кода иллюстрирует редактирование записи в таблице <xref:System.Data.DataTable> и затем вызов метода `TableAdapter.Update` для сохранения изменений в базе данных.  \(Этот пример использует таблицу Region базы данных "Борей"\).  
  
     [!code-vb[VbRaddataSaving#17](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#17](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_1.cs)]  
  
 Если приложение использует объекты для хранения данных в приложении, можно использовать методы `DBDirect` TableAdapter для отправки данных из объектов прямо в базу данных.  Эти методы позволяют передавать отдельные значения для каждого столбца в качестве параметров метода.  Вызов этого метода обновляет существующую запись в базе данных значениями столбца, передаваемыми в метод.  
  
 В следующей процедуре в качестве примера используется таблица `Region` базы данных "Борей".  
  
#### Для обновления записей в базе данных с помощью метода TableAdapter.Update, который принимает значения столбцов:  
  
-   Вызовите метод адаптера таблиц `Update`, передав в него новые и оригинальные значения для каждого столбца в качестве параметров.  
  
    > [!NOTE]
    >  Если у вас нет экземпляра адаптера таблиц, создайте экземпляр, который вы хотели бы использовать.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_2.cs)]  
  
## Обновление записей с помощью командных объектов  
 В следующем примере обновляются существующие записи непосредственно в базе данных с помощью командных объектов.  Дополнительные сведения по использованию объектов команд для выполнения команд и хранимых процедур содержатся в разделе [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md).  
  
 В следующей процедуре в качестве примера используется таблица `Region` базы данных "Борей".  
  
#### Чтобы обновить существующие записи в базе данных с помощью командных объектов:  
  
-   Создайте новый командный объект; задайте его свойства `Connection`, `CommandType` и `CommandText`; затем откройте подключение и выполните команду.  
  
     [!code-vb[VbRaddataSaving#19](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#19](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_3.cs)]  
  
## Безопасность платформы .NET Framework  
 Необходимо иметь доступ к базе данных, к которой вы пытаетесь подключиться, а также разрешение на обновление записей в нужной таблице.  
  
## См. также  
 [Общие сведения об адаптере таблиц](../data-tools/tableadapter-overview.md)   
 [Практическое руководство. Удаление записей из базы данных](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [Практическое руководство. Вставка новых записей в базу данных](../data-tools/insert-new-records-into-a-database.md)   
 [Практическое руководство. Сохранение данных из объекта в базе данных](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Общие сведения о приложениях для работы с данными в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Сохранение данных](../data-tools/saving-data.md)