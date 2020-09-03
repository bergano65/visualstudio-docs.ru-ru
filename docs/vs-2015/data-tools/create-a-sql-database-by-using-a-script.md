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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670082"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Создание базы данных SQL с помощью скрипта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве используется Visual Studio для создания небольшой базы данных, содержащей пример кода для [создания простого приложения](../data-tools/create-a-simple-data-application-by-using-adonet.md)для работы с данными с помощью ADO.NET.

 **Содержание раздела**

- [создание скрипта со схемой базы данных](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript);

- [Создание проекта базы данных и импорт схемы](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [Развертывание базы данных](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения инструкций из этого пошагового руководства необходимо установить SQL Server Express LocalDB или другую базу данных SQL.

## <a name="create-a-script-that-contains-a-database-schema"></a><a name="CreateScript"></a> Создание скрипта, содержащего схему базы данных

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Создание скрипта, из которого можно импортировать схему

1. В в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] строке меню выберите **файл**  >  **создать**  >  **файл**.

     Откроется диалоговое окно **Создание файла** .

2. В списке **категории** выберите **Общие**.

3. В списке **шаблоны** выберите **SQL File**, а затем нажмите кнопку **Открыть** .

     Откроется редактор Transact-SQL.

4. Скопируйте следующий код Transact-SQL и вставьте его в редактор Transact-SQL.

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

5. В строке меню выберите **файл**  >  **сохранить SqlQuery_1. SQL как**.

     Откроется диалоговое окно **сохранить файл как** .

6. В поле **имя файла** введите `SampleImportScript.sql` , запишите расположение, где будет сохранен файл, а затем нажмите кнопку **сохранить** .

7. В строке меню выберите **файл**  >  **Закрыть решение**.

     Затем создайте проект базы данных, а затем импортируйте схему из созданного скрипта.

## <a name="create-a-database-project-and-import-a-schema"></a><a name="CreateProject"></a> Создание проекта базы данных и импорт схемы

#### <a name="to-create-a-database-project"></a>Создание проекта базы данных

1. В строке меню выберите **Файл** > **Новый** > **Проект**.

     Откроется диалоговое окно **Новый проект** .

2. В разделе **установленные**разверните узел **шаблоны** , разверните узел **другие языки** , выберите категорию **SQL Server** , а затем выберите шаблон **проекта базы данных SQL Server** .

    > [!NOTE]
    > Узел **другие языки** не отображается во всех установках Visual Studio.

3. В поле **имя** введите `Small Database` .

4. Установите флажок **создать каталог для решения** , если он еще не выбран.

5. Снимите флажок **Добавить в систему управления версиями** , если он еще не снят, а затем нажмите кнопку **ОК** .

     Проект базы данных будет создан и отображен в **обозревателе решений**.

     Затем импортируйте схему базы данных из скрипта.

#### <a name="to-import-a-database-schema-from-a-script"></a>Импорт схемы базы данных из скрипта

1. В строке меню выберите **проект**  >  **Импорт**  >  **скрипта**.

2. На странице **Приветствие** просмотрите текст, а затем нажмите кнопку **Далее** .

3. Выберите параметр **один файл** , а затем нажмите кнопку **Обзор** .

     Откроется диалоговое окно **Импорт скрипта SQL** .

4. Откройте папку, в которую был сохранен файл Самплеимпортскрипт. SQL, выберите файл, а затем нажмите кнопку **Открыть** .

5. Нажмите кнопку **Готово** , чтобы закрыть диалоговое окно **Импорт скрипта SQL** .

     Скрипт импортируется, и объекты, которые определяет скрипт, добавляются в проект базы данных.

6. Просмотрите сводку и нажмите кнопку **"Готово** ", чтобы закрыть диалоговое окно " **Импорт файла скрипта SQL** ".

7. В **Обозреватель решений**разверните папки Sales, Scripts и Security проекта и убедитесь, что они содержат файлы. SQL.

8. В **Обозреватель объектов SQL Server**убедитесь, что база данных отображается в узле **проекты** .

     На этом этапе база данных содержит только системные объекты, такие как таблицы и хранимые процедуры. После развертывания база данных будет содержать пользовательские таблицы и хранимые процедуры, определяемые скриптами.

## <a name="deploy-the-database"></a><a name="DeployDatabase"></a> Развертывание базы данных
 При нажатии клавиши **F5** по умолчанию развертывается (или публикуется) база данных в базе данных LocalDB. Базу данных можно развернуть в другом расположении, открыв страницу свойств проекта, выбрав вкладку **Отладка** , а затем изменив строку подключения.
