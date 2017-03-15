---
title: "Пошаговое руководство. Создание хранимых процедур обновления данных для таблицы Customers базы данных Northwind | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "учебная база данных Northwind"
  - "реляционный конструктор объектов, хранимые процедуры"
  - "хранимые процедуры [Visual Studio]"
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Пошаговое руководство. Создание хранимых процедур обновления данных для таблицы Customers базы данных Northwind
В некоторых разделах справки в документации по [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] требуется использование дополнительных хранимых процедур в учебной базе данных "Борей" для выполнения обновлений \(вставки, обновления и удаления\) данных в таблице "Клиенты".  
  
 В данном пошаговом руководстве приведены указания по созданию таких дополнительных хранимых процедур в учебных базах данных "Борей" для [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  
  
 В подразделе "Следующие шаги" данного раздела приведены ссылки на разделы, где описываются принципы работы с этими дополнительными хранимыми процедурами.  
  
 В рамках данного пошагового руководства вы узнаете, как выполнять следующие задачи.  
  
-   Создание подключения к данным для учебной базы данных "Борей".  
  
-   Создание хранимых процедур.  
  
## Обязательные компоненты  
 Для выполнения данного пошагового руководства требуется:  
  
-   Доступ к версии SQL Server учебной базы данных "Борей".  Для получения дополнительной информации см. [Практическое руководство. Установка образцов баз данных](../data-tools/how-to-install-sample-databases.md).  
  
## Подключение к базе данных "Борей"  
 В рамках данного пошагового руководства требуется подключение к версии SQL Server базы данных "Борей".  В описании следующей процедуры приведены указания по созданию нужного подключения к данным.  
  
> [!NOTE]
>  Если вы уже установили подключение к данным для базы данных "Борей", можете перейти к следующему подразделу "Создание хранимых процедур".  
  
#### Создание подключения к данным для базы данных "Борей" SQL Server  
  
1.  В меню **Вид** выберите **Обозреватель серверов**\/**Обозреватель баз данных**.  
  
2.  Щелкните правой кнопкой мыши элемент **Подключения данных** и выберите пункт **Добавить подключение**.  
  
3.  В диалоговом окне **Выбор источника данных** выберите **Microsoft SQL Server** и нажмите кнопку **ОК**.  
  
     Если отображается диалоговое окно **Добавить подключение**, а **Источник данных** отличается от **Microsoft SQL Server \(SqlClient\)**, щелкните элемент **Изменить**, чтобы открыть диалоговое окно **Выбор источника данных\/Сменить источник данных**, выберите **Microsoft SQL Server** и нажмите кнопку **ОК**.  
  
4.  Щелкните **Имя сервера** в раскрывающемся списке или введите имя сервера, на котором расположена база данных "Борей".  
  
5.  В зависимости от требований базы данных или приложения либо щелкните **Использовать аутентификацию Windows**, либо используйте определенное имя пользователя и определенный пароль для входа на компьютер с запущенной системой SQL Server \(**Аутентификация SQL Server**\).  
  
6.  Щелкните базу данных "Борей" в списке **Выберите или введите имя базы данных**.  
  
7.  Нажмите кнопку **ОК**.  
  
     Подключение к данным добавляется в **Обозреватель серверов**\/**Обозреватель баз данных**.  
  
## Создание хранимых процедур  
 Создайте хранимые процедуры, запустив предложенный скрипт SQL для базы данных "Борей", для этого используйте [Визуальные инструменты для баз данных](http://msdn.microsoft.com/ru-ru/6b145922-2f00-47db-befc-bf351b4809a1), доступные в **Обозревателе серверов**\/**Обозревателе баз данных**.  
  
#### Создание хранимых процедур с помощью скрипта SQL  
  
1.  Разверните базу данных "Борей" в **Обозревателе серверов**\/**Обозревателе баз данных**.  
  
2.  Щелкните узел **Хранимые процедуры** правой кнопкой мыши и выберите пункт **Добавить новую хранимую процедуру**.  
  
3.  Вставьте следующий код в редактор кода, заменив шаблон `CREATE PROCEDURE`:  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Выберите весь текст в редакторе кода, щелкните выбранный текст правой кнопкой мыши и выберите пункт **Выполнить выбранное**.  
  
     Для базы данных "Борей" создаются хранимые процедуры SelectCustomers, InsertCustomers, UpdateCustomers и DeleteCustomers.  
  
## Следующие действия  
 Для изучения принципов работы с хранимыми процедурами после их создания обратитесь к следующим пошаговым руководствам:  
  
 [Как назначить хранимые процедуры для выполнения обновлений, вставок и удалений \(реляционный конструктор объектов\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Пошаговое руководство. Создание классов LINQ to SQL \(реляционный конструктор объектов\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [Пошаговое руководство. Настройка операций вставки, обновления и удаления в классах сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## См. также  
 [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)