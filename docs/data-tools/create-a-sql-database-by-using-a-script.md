---
title: "Пошаговое руководство. Создание небольшого примера базы данных | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Пошаговое руководство. Создание небольшого примера базы данных
В данном пошаговом руководстве используется Visual Studio, чтобы создать небольшую базу данных, которая содержит пример кода для [Пошаговое руководство. Создание простого приложения для работы с данными с помощью ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **Содержание раздела**  
  
-   [Создание скрипта, содержащего схему базы данных.](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Создание проекта базы данных и импорт схемы](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Развертывание базы данных](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## Обязательные компоненты  
 Для выполнения инструкций данного пошагового руководства требуется установленная [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  Необходимо также иметь возможность подключиться к серверу базы данных или базе данных LocalDB, где у вас есть разрешения на создание и развертывание базы данных.  
  
##  <a name="CreateScript"></a> Создание скрипта, содержащего схему базы данных.  
  
#### Создание скрипта, из которого можно импортировать схему  
  
1.  В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в строке меню выберите **Файл**, **Создать**, **Файл**.  
  
     Появится диалоговое окно **Создание файла**.  
  
2.  В списке **Категории** выберите **Общие**.  
  
3.  В списке **Шаблоны** выберите **SQL\-файл**, а затем нажмите кнопку **Открыть**.  
  
     Появится редактор Редактор Transact\-SQL.  
  
4.  Скопируйте приведенный ниже код Transact\-SQL и вставьте его в редактор Transact\-SQL.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  В меню **Файл** выберите **Сохранить SqlQuery\_1.sql как**.  
  
     Откроется диалоговое окно **Сохранить файл как**.  
  
6.  В поле **Имя файла** введите `SampleImportScript.sql`, запомните расположение, в котором будет сохранен файл, а затем нажмите кнопку **Сохранить**.  
  
7.  В меню **Файл** выберите **Закрыть решение**.  
  
     Затем создайте проект базы данных и импортируйте схему из только что созданного скрипта.  
  
##  <a name="CreateProject"></a> Создание проекта базы данных и импорт схемы  
  
#### Создание проекта базы данных  
  
1.  В меню **Файл** выберите **Создать**, **Проект**.  
  
     Откроется диалоговое окно **Новый проект**.  
  
2.  В разделе **Установленные** разверните узел **Шаблоны**, разверните узел **Другие языки** выберите категорию **SQL Server**, а затем выберите шаблон **Проект базы данных SQL Server**.  
  
    > [!NOTE]
    >  Узел **Другие языки** не виден во всех установки Visual Studio.  
  
3.  В поле **Имя** введите `Small Database`.  
  
4.  Установите флажок **Создать каталог для решения**, если он еще не установлен.  
  
5.  Снимите флажок **Добавить в систему управления версиями**, если он установлен, и нажмите кнопку **ОК**.  
  
     В **обозревателе решений** отобразится созданный проект.  
  
     Далее импортируйте схему базы данных из скрипта.  
  
#### Импорт схемы базы данных из скрипта  
  
1.  В меню **Проект** выберите **Импорт**, **Скрипт**.  
  
2.  На странице приветствия прочитайте текст и нажмите кнопку **Далее**.  
  
3.  Выберите переключатель **Отдельный файл**, а затем нажмите кнопку **Обзор**.  
  
     Откроется диалоговое окно **Импорт скрипта SQL**.  
  
4.  Откройте папку, где сохранен файл SampleImportScript.sql, выберите его и затем нажмите кнопку **Открыть**.  
  
5.  Нажмите кнопку **Готово**, чтобы закрыть диалоговое окно **Импорт скрипта SQL**.  
  
     Скрипт будет импортирован, и объекты, определенные в этом скрипте, будут добавлены в проект базы данных.  
  
6.  Просмотр сводки, а затем нажмите кнопку **Готово**, чтобы закрыть диалоговое окно **Импорт файла скрипта SQL**.  
  
7.  В поле **Обозреватель решений** разверните папки "Сбыт", "Скрипты" и "Безопасность" вашего проекта и убедитесь, что они содержат файлы SQL.  
  
8.  В поле **Обозреватель объектов SQL Server** убедитесь, что база данных находится в узле **Проекты**.  
  
     На этом этапе база данных содержит только системные объекты, такие как таблицы и хранимые процедуры.  После развертывания базы данных она будет содержать пользовательские таблицы и хранимые процедуры, определяемые скриптами.  
  
##  <a name="DeployDatabase"></a> Развертывание базы данных  
 При нажатии клавиши F5 развертывается или публикуется база данных в базу данных LocalDB по умолчанию.  Можно развернуть базу данных в другое место, откройте страницы свойств для проекта, выберите вкладку **Отладка**, а затем изменить строку подключения.