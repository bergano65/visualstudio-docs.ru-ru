---
title: Установка образцов баз данных SQL Server | Документация Майкрософт
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3915351bff74f35ceb5fc462cb29dfd2f322fb6a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299636"
---
# <a name="install-sql-server-sample-databases"></a>Установка образцов баз данных SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Образцы баз данных полезны для экспериментов с запросами SQL и LINQ, DataBinding, Entity Framework моделирования и т. д.  Каждый продукт базы данных имеет собственные образцы баз данных. Northwind и AdventureWorks — это два популярных образца баз данных SQL Server.

 **AdventureWorks** — это текущий образец базы данных, предоставляемый для продуктов SQL Server. Его можно скачать в виде MDF-файла на [странице AdventureWorks на сайте CodePlex](https://archive.codeplex.com/?p=msftdbprodsamples). Существуют обычные и упрощенные (LT) версии базы данных, доступные здесь. В большинстве случаев предпочтительнее использовать версию LT, поскольку она менее сложная.

 **Northwind** — это относительно простая SQL Server база данных, которая использовалась в течение многих лет. Его можно скачать как bak-файл на [странице базы данных Northwind на сайте CodePlex](https://northwinddatabase.codeplex.com/). Чтобы избежать проблем с разрешениями, распакуйте файл в новую папку, которая не находится в папке пользователя.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Восстановление базы данных из BAK-файла в Visual Studio

1. При создании резервной копии Microsoft SQL Server базы данных результатом является bak-файл. Чтобы файл BAK снова можно было использовать в качестве файла базы данных, его необходимо *восстановить*. В главном меню выберите **View** > **Обозреватель объектов SQL Server**. Если вы не видите его, возможно, потребуется установить его. Перейдите в **Панель управления** > **программы и компоненты**, найдите Microsoft Visual Studio 2015 и нажмите кнопку **изменить** . Когда список установленных компонентов появится в окне установщика, установите флажок **Обозреватель объектов SQL Server** и продолжайте установку.

2. В обозреватель объектов SQL Server щелкните правой кнопкой мыши любой SQL Server ядро СУБД (например, LocalDB) и выберите**создать запрос**.

     ![обозреватель объектов SQL Server новый запрос](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "раддата обозреватель объектов SQL Server новый запрос")

3. Во первых, вам потребуются логические имена файлов базы данных и журнала внутри файла BAK. Чтобы получить его, введите этот запрос в редакторе SQL Server, а затем нажмите зеленую кнопку **выполнить** в верхней части окна. При необходимости измените путь к файлу, чтобы он указывал на bak.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     Запишите логические имена, которые отображаются в окне результатов.  Для базы данных Northwind используются два логических имени: Northwind и Northwind_log.

4. Теперь выполните этот запрос, чтобы создать базу данных. При необходимости замените исходные и конечные пути, имена логических баз данных и физические имена файлов для базы данных Northwind. Обеспечьте расширение файлов MDF и LDF.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. В обозреватель объектов SQL Server щелкните правой кнопкой мыши узел базы **данных** , и вы увидите узел базы данных Northwind. В противном случае щелкните правой кнопкой мыши базы данных и выберите команду **Добавить новую базу данных**. Введите имя и расположение только что созданного MDF – файла.

6. Теперь база данных готова к использованию в качестве источника данных в Visual Studio.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Восстановление базы данных из BAK-файла в SQL Server Management Studio

1. Скачайте SQL Server Management Studio с сайта загрузки.

2. В окне **обозревателя объектов** SSMS щелкните правой кнопкой мыши узел **базы данных** , выберите команду**восстановить базу данных**и укажите расположение BAK-файла.

     ![Восстановление базы данных SSMS](../data-tools/media/raddata-ssms-restore-database.png "Восстановление базы данных раддата SSMS")
