---
title: "Практическое руководство. Непосредственный доступ к базе данных с помощью адаптера таблицы | Microsoft Docs"
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
  - "базы данных [Visual Basic], обращение с помощью адаптера таблицы"
  - "наборы данных [Visual Basic], добавление в проекты"
  - "DBDirect - методы"
  - "GenerateDbDirectMethods - свойство"
  - "сохранение данных"
  - "TableAdapter.Delete - метод"
  - "TableAdapter.GenerateDBDirectMethods - свойство"
  - "TableAdapter.Insert - метод"
  - "TableAdapter.Update - метод"
  - "адаптеры таблиц TableAdapter"
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Непосредственный доступ к базе данных с помощью адаптера таблицы
В дополнение к `InsertCommand`, `UpdateCommand` и `DeleteCommand`, адаптеры таблиц создаются с помощью методов, которые могут быть выполнены непосредственно в базе данных.  Эти методы \(`TableAdapter.Insert`, `TableAdapter.Update` и `TableAdapter.Delete`\) можно вызывать напрямую для работы с данными в базе данных.  
  
 Если нет необходимости создавать эти непосредственные методы, назначьте свойству `GenerateDbDirectMethods` адаптера таблиц значение `false` в окне **Свойства**.  Все запросы, добавляемые к адаптеру таблиц в дополнение к основным запросам, являются автономными, т.е. не создают эти методы DbDirect.  
  
## Непосредственная отправка команды к базе данных  
 Вызовите метод адаптера таблиц DbDirect, который решает требуемую задачу.  
  
#### Для непосредственной вставки новых записей в базу данных  
  
-   Вызовите метод адаптера таблиц `Insert`, передав значения для каждого столбца в качестве параметров.  В следующей процедуре в качестве примера используется таблица `Region` базы данных Northwind.  
  
    > [!NOTE]
    >  Если у вас нет экземпляра адаптера таблиц, создайте экземпляр требуемого адаптера.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### Чтобы обновить записи непосредственно в базе данных  
  
-   Вызовите метод адаптера таблиц `Update`, передав в него новые и оригинальные значения для каждого столбца в качестве параметров.  
  
    > [!NOTE]
    >  Если у вас нет экземпляра адаптера таблиц, создайте экземпляр требуемого адаптера.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### Для удаления записей непосредственно из базы данных  
  
-   Вызовите метод адаптера таблиц `Delete`, передав значения для каждого столбца в качестве параметров метода `Delete`.  \(Этот пример использует таблицу `Region` базы данных Northwind.\)  
  
    > [!NOTE]
    >  Если у вас нет экземпляра адаптера таблиц, создайте экземпляр требуемого адаптера.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## См. также  
 [Общие сведения о приложениях для работы с данными в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Сохранение данных](../data-tools/saving-data.md)   
 [Общие сведения об адаптере таблиц](../data-tools/tableadapter-overview.md)   
 [Команды и параметры](../Topic/Commands%20and%20Parameters.md)