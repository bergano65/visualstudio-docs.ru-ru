---
title: 'Пошаговое руководство: Создание хранимых процедур обновления для таблицы Customers "Борей" | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
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
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: bbcd68b7604f7a80546168406146f326e1bac224
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557924"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>Пошаговое руководство. Создание хранимых процедур обновления данных для таблицы Customers базы данных Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Некоторые разделы справки в [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] документации требуют дополнительных хранимых процедур в базе данных Northwind для выполнения обновлений (вставки, обновления и удаления) данных в таблице Customers.  
  
 В данном пошаговом руководстве приведены указания по созданию таких дополнительных хранимых процедур в учебных базах данных "Борей" для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 В подразделе "Следующие шаги" данного раздела приведены ссылки на разделы, где описываются принципы работы с этими дополнительными хранимыми процедурами.  
  
 В рамках данного пошагового руководства вы узнаете, как выполнять следующие задачи.  
  
-   Создание подключения к данным для учебной базы данных "Борей".  
  
-   Создание хранимых процедур.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
-   Доступ к версии SQL Server учебной базы данных "Борей". Дополнительные сведения см. в разделе [как: установить образцы баз данных](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="connecting-to-the-northwind-database"></a>Подключение к базе данных "Борей"  
 В рамках данного пошагового руководства требуется подключение к версии SQL Server базы данных "Борей". В описании следующей процедуры приведены указания по созданию нужного подключения к данным.  
  
> [!NOTE]
>  Если вы уже установили подключение к данным для базы данных "Борей", можете перейти к следующему подразделу "Создание хранимых процедур".  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>Создание подключения к данным для базы данных "Борей" SQL Server  
  
1.  На **представление** меню, щелкните **обозревателя серверов**/**обозреватель баз данных**.  
  
2.  Щелкните правой кнопкой мыши **подключения к данным** и нажмите кнопку **добавить подключение**.  
  
3.  В **Выбор источника данных** диалоговом окне щелкните **Microsoft SQL Server**, а затем нажмите кнопку **ОК**.  
  
     Если **добавить подключение** откроется диалоговое окно и **источника данных** не **Microsoft SQL Server (SqlClient)**, нажмите кнопку **изменение** для открытия **Выбор/Смена источника данных** диалоговом окне щелкните **Microsoft SQL Server**, а затем нажмите кнопку **ОК**.  
  
4.  Нажмите кнопку **имя сервера** в раскрывающемся списке или введите имя сервера, на котором расположена база данных "Борей".  
  
5.  В зависимости от требований базы данных или приложения либо щелкните **используйте проверку подлинности Windows** или использовать указанные имя пользователя и пароль для входа на компьютер с запущенной системой SQL Server (**проверку подлинности SQL Server**).  
  
6.  Щелкните базу данных "Борей" в **выберите или введите имя базы данных** списка.  
  
7.  Нажмите кнопку **ОК**.  
  
     Подключение к данным добавляется **обозревателя серверов**/**обозреватель баз данных**.  
  
## <a name="creating-the-stored-procedures"></a>Создание хранимых процедур  
 Создание хранимых процедур, запустив предложенный скрипт SQL в базе данных "Борей" с помощью [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) в **обозревателя серверов** /  **Проводника баз данных**.  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>Создание хранимых процедур с помощью скрипта SQL  
  
1.  Разверните базу данных "Борей" в **обозревателя серверов**/**обозреватель баз данных**.  
  
2.  Щелкните правой кнопкой мыши **хранимые процедуры** узел и нажмите кнопку **добавить новую хранимую процедуру**.  
  
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
  
4.  Выделите весь текст в редакторе кода, щелкните правой кнопкой мыши выделенный текст и нажмите кнопку **выполнить выделенный фрагмент**.  
  
     Для базы данных "Борей" создаются хранимые процедуры SelectCustomers, InsertCustomers, UpdateCustomers и DeleteCustomers.  
  
## <a name="next-steps"></a>Следующие шаги  
 Для изучения принципов работы с хранимыми процедурами после их создания обратитесь к следующим пошаговым руководствам:  
  
 [Практическое руководство. Назначение хранимых процедур для выполнения обновления, вставки и удаления (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [Пошаговое руководство. Настройка поведения вставки, обновления и удаления классов сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)