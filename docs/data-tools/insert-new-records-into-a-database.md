---
title: "Практическое руководство. Вставка новых записей в базу данных | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "базы данных, вставка новых записей в"
  - "записи, вставка"
  - "сохранение данных"
  - "адаптеры таблиц TableAdapter, вставка новых записей в"
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Вставка новых записей в базу данных
Для вставки новых записей в базу данных можно использовать метод `TableAdapter.Update` или один из методов адаптера таблиц DBDirect \(в частности метод `TableAdapter.Insert`\).  Дополнительные сведения см. в разделе [Общие сведения об адаптере таблиц](../data-tools/tableadapter-overview.md).  
  
 Если приложение не использует адаптеры таблиц, то для взаимодействия и вставки новых записей в базе данных можно использовать командные объекты \(например <xref:System.Data.SqlClient.SqlCommand>\).  
  
 Используйте метод `TableAdapter.Update`, если приложение использует для хранения данных наборы данных.  Метод `Update` передает все изменения \(обновления, вставки и удаления\) в базу данных.  
  
 Применяйте метод `TableAdapter.Insert`, если приложение использует для хранения данных объекты, или когда требуется детальный контроль над созданием новых записей в базе данных.  
  
 Если адаптер таблиц не имеет метода `Insert`, это означает, что либо он настроен на использование сохраненных процедур, или свойство `GenerateDBDirectMethods` имеет значение `false`.  Попробуйте присвоить свойству `GenerateDBDirectMethods` адаптера таблиц TableAdapter значение `true` из [Конструктора наборов данных](../data-tools/creating-and-editing-typed-datasets.md) и затем сохранить набор данных, чтобы заново создать адаптер таблиц.  Если адаптер таблиц по\-прежнему не имеет метода `Insert`, то таблица, скорее всего, не предоставляет достаточно сведений о схеме для различения отдельных строк \(например нет первичного ключа\).  
  
## Вставка новых записей с помощью адаптеров таблиц  
 Адаптеры таблиц предоставляют различные способы вставки новых записей в базу данных в зависимости от требований приложения.  
  
 Если приложение использует для хранения данных наборы данных, можно просто добавлять данные в нужную таблицу <xref:System.Data.DataTable> в наборе данных, а затем вызвать метод `TableAdapter.Update`.  Метод `TableAdapter.Update` принимает любые изменения в <xref:System.Data.DataTable> и отправляет эти изменения в базу данных \(включая измененные и удаленные записи\).  
  
#### Для вставки новых записей в базу данных с помощью метода TableAdapter.Update:  
  
1.  Добавьте новые записи в нужные таблицы <xref:System.Data.DataTable> путем создания новых строк <xref:System.Data.DataRow> и добавления их к коллекции <xref:System.Data.DataTable.Rows%2A>.  Дополнительные сведения см. в разделе [Практическое руководство. Добавление строк в объект DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).  
  
2.  После добавления новых строк в <xref:System.Data.DataTable> вызовите метод `TableAdapter.Update`.  Можно контролировать объем данных для обновления путем передачи всего <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, массива <xref:System.Data.DataRow> или одной <xref:System.Data.DataRow>.  
  
     Следующий фрагмент кода иллюстрирует добавление новой записи в <xref:System.Data.DataTable> и вызов метода `TableAdapter.Update`, чтобы сохранить новую строку в базе данных.  \(В этом примере используется таблица `Region` базы данных "Борей"\).  
  
     [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
 Если приложение использует для хранения данных объекты, то для создания новых строк непосредственно в базе данных можно использовать метод `TableAdapter.Insert`.  Метод `Insert` принимает отдельные значения для каждого столбца в качестве параметров.  При вызове метода новая запись вставляется в базу данных с передаваемыми значениями параметров.  
  
 В следующей процедуре в качестве примера используется таблица `Region` базы данных Northwind.  
  
#### Для вставки новых записей в базу данных с помощью метода TableAdapter.Insert:  
  
-   Вызовите метод адаптера таблиц `Insert`, передав значения для каждого столбца в качестве параметров.  
  
    > [!NOTE]
    >  Если у вас нет экземпляра адаптера таблиц, создайте экземпляр, который вы хотели бы использовать.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## Вставка новых записей с помощью командных объектов  
 В следующем примере новые записи вставляются непосредственно в базу данных с помощью командных объектов.  Дополнительные сведения по использованию объектов команд для выполнения команд и хранимых процедур содержатся в разделе [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md).  
  
 В следующей процедуре в качестве примера используется таблица `Region` базы данных Northwind.  
  
#### Для вставки новых записей в базу данных с помощью командных объектов:  
  
-   Создайте новый командный объект, задав его свойства `Connection`, `CommandType` и `CommandText`.  
  
     [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## Безопасность платформы .NET Framework  
 Необходимо иметь доступ к базе данных, к которой вы пытаетесь подключиться, а также разрешение на вставку записей в нужную таблицу.  
  
## См. также  
 [Практическое руководство. Удаление записей из базы данных](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [Практическое руководство. Обновление записей в базе данных](../data-tools/how-to-update-records-in-a-database.md)   
 [Практическое руководство. Сохранение данных из объекта в базе данных](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Общие сведения о приложениях для работы с данными в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Сохранение данных](../data-tools/saving-data.md)   
 [Получение значений идентификаторов или автонумерации](../Topic/Retrieving%20Identity%20or%20Autonumber%20Values.md)