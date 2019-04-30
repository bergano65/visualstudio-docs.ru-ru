---
title: Создание базы данных SQL с помощью скрипта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7c0dc7b406f7e04aaa9848e2f5dcb96f17430f6d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436959"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Создание базы данных SQL с помощью скрипта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве используется Visual Studio для создания небольших баз данных, который содержит образец кода для [Создание простых данных приложения с помощью ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **Содержание раздела**  
  
- [Создайте сценарий, который содержит схему базы данных](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
- [Создать проект базы данных и импорт схемы](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
- [Развертывание базы данных](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства, необходимо иметь SQL Server Express LocalDB или другой базы данных SQL, установлены.  
  
## <a name="CreateScript"></a> Создайте сценарий, который содержит схему базы данных  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Чтобы создать сценарий, из которого можно импортировать схему  
  
1. В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], в строке меню выберите **файл** > **New** > **файл**.  
  
     **Новый файл** откроется диалоговое окно.  
  
2. В **категории** выберите **Общие**.  
  
3. В **шаблоны** выберите **файл Sql**, а затем выберите **откройте** кнопки.  
  
     Откроется редактор Transact-SQL.  
  
4. Скопируйте приведенный ниже код Transact-SQL, а затем вставьте его в редакторе Transact-SQL.  
  
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
  
5. В строке меню выберите **файл** > **Сохранить SqlQuery_1.sql как**.  
  
     **Сохранить файл как** откроется диалоговое окно.  
  
6. В **имя файла** введите `SampleImportScript.sql`, запишите расположение, где будет сохранить файл, а затем выберите **Сохранить** кнопки.  
  
7. В строке меню выберите **файл** > **закрыть решение**.  
  
     Затем создайте проект базы данных и затем импортировать схему из сценария, который вы создали.  
  
## <a name="CreateProject"></a> Создать проект базы данных и импорт схемы  
  
#### <a name="to-create-a-database-project"></a>Создание проекта базы данных  
  
1. В строке меню выберите **Файл** > **Создать** > **Проект**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
2. В разделе **установленные**, разверните **шаблоны** узел, разверните **другие языки** выберите **SQL Server** категории, а затем Выберите **проект базы данных SQL Server** шаблона.  
  
    > [!NOTE]
    > **Другие языки** узла не отображается во всех установках Visual Studio.  
  
3. В **имя** введите `Small Database`.  
  
4. Выберите **создать каталог для решения** флажок, если он еще не открыт.  
  
5. Очистить **добавить в систему управления версиями** флажок, если он еще не снят, а затем выберите **ОК** кнопки.  
  
     Проект базы данных создается и отображается в **обозревателе решений**.  
  
     Затем можно импортируйте схему базы данных из скрипта.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>Чтобы импортировать схему базы данных из скрипта  
  
1. В строке меню выберите **проекта** > **импорта** > **скрипт**.  
  
2. На **приветствия** странице, ознакомьтесь с текстом, а затем выберите **Далее** кнопки.  
  
3. Выберите **один файл** переключатель, а затем выберите **Обзор** кнопки.  
  
     **Импорт скрипта SQL** откроется диалоговое окно.  
  
4. Откройте папку, где был сохранен файл SampleImportScript.sql, выберите файл и затем выберите **откройте** кнопки.  
  
5. Выберите **Готово** кнопку, чтобы закрыть **Импорт скрипта SQL** диалоговое окно.  
  
     Скрипт будет импортирован, и объекты, которые сценарий определяет, будут добавлены в проект базы данных.  
  
6. Просмотрите сводные данные и нажмите кнопку **Готово** кнопку, чтобы закрыть **импорта файла скрипта SQL** диалоговое окно.  
  
7. В **обозревателе решений**, разверните узел Sales, сценарии и безопасности папки проекта и убедитесь, что они содержат файлы SQL.  
  
8. В **обозреватель объектов SQL Server**, убедитесь, что базы данных отображается в разделе **проекты** узла.  
  
     На этом этапе база данных содержит только системные объекты, такие как таблицы и хранимые процедуры. После развертывания базы данных, он будет содержать пользовательские таблицы и хранимые процедуры, определяемые скриптами.  
  
## <a name="DeployDatabase"></a> Развертывание базы данных  
 При нажатии клавиши **F5** ключ, развертывание (или публикация) базы данных в базу данных LocalDB по умолчанию. Можно развернуть базу данных в другое место, откройте страницу свойств проекта, выбрав **Отладка** вкладку, а затем изменить строку подключения.
