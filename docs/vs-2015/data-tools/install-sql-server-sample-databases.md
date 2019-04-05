---
title: Установка образцов баз данных SQL Server | Документация Майкрософт
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2fc172e9ed91a354918fd536060f97fcbb259a94
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980653"
---
# <a name="install-sql-server-sample-databases"></a>Установка образцов баз данных SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Образцы баз данных полезны для экспериментов с запросы SQL и LINQ, привязка данных, моделирование Entity Framework и т. д.  Каждый продукт базы данных имеет свои собственные образцы баз данных. Northwind и AdventureWorks являются две популярные SQL Server образцы баз данных.  
  
 **AdventureWorks** является текущей базе данных для продуктов SQL Server. Его можно загрузить в виде MDF-файла из [страницы AdventureWorks в Codeplex](http://msftdbprodsamples.codeplex.com/). Доступны регулярные и простой (LT) версии базы данных здесь. В большинстве случаев LT версии является предпочтительным, так как он был менее сложным.  
  
 **Northwind** — это относительно простой база данных SQL Server, который использовался в течение многих лет. Его можно загрузить в виде файла BAK-файл из [странице базы данных "Борей" на сайте CodePlex](https://northwinddatabase.codeplex.com/). Чтобы избежать проблем с разрешениями, распакуйте файл в новую папку, в которое не находится под папки пользователя.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Восстановление базы данных из файла BAK-файл в Visual Studio  
  
1.  При создании резервной копии базы данных Microsoft SQL Server, то результатом является BAK-файле. Чтобы сделать BAK-файл, который файл можно использовать повторно в файле базы данных, он должен быть *восстановить*. В главном меню выберите **представление** > **обозреватель объектов SQL Server**. Если вы не видите его, может потребоваться установить его. Перейдите к **панели управления** > **программы и компоненты**найдите Microsoft Visual Studio 2015 и нажмите кнопку **изменение** кнопки. В открывшемся списке установленных компонентов в окне установщика выберите **обозреватель объектов SQL Server** установите флажок, а затем продолжите установку.  
  
2.  В обозревателе объектов SQL Server, щелкните правой кнопкой мыши любой ядра СУБД SQL Server (например, localdb) и выберите**новый запрос**.  
  
     ![Новый запрос обозреватель объектов SQL Server](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata новый запрос обозреватель объектов SQL Server")  
  
3.  Во-первых необходимо логические имена файлов базы данных и журнала в BAK-файле. Чтобы получить его, введите этот запрос в редакторе запросов SQL, а затем выберите зеленый **запуска** кнопку в верхней части окна. Измените путь к файлу, при необходимости, чтобы он указывал BAK-файле.  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     Запишите логические имена, которые отображаются в окне результатов.  Для базы данных Northwind две логические имена, которые Northwind и Northwind_log.  
  
4.  Теперь выполните этот запрос для создания базы данных. Подставьте собственные пути источника и назначения, логические имена баз данных и имена физических файлов для Northwind соответствующим образом. Сохраните файлы MDF и LDF расширений файлов.  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5.  В обозревателе объектов SQL Server, щелкните правой кнопкой мыши **баз данных** узел и вы увидите узел базы данных "Борей". Если это не так, щелкните правой кнопкой мыши баз данных и выберите **добавить новую базу данных**. Введите имя и расположение MDF-файла, который вы только что создали.  
  
6.  Базы данных теперь готов для использования в качестве источника данных в Visual Studio.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Восстановление базы данных из файла BAK-файл в SQL Server Management Studio  
  
1.  Скачайте SQL Server Management Studio с сайта загрузки.  
  
2.  В SSMS **обозревателя объектов** окно, щелкните правой кнопкой мыши **баз данных** выберите**Restore Database**и указать расположение файла BAK-файл.  
  
     ![Восстановление базы данных SSMS](../data-tools/media/raddata-ssms-restore-database.png "raddata SSMS восстановление базы данных")
