---
title: 'Как: установить образцы баз данных | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
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
- sample databases, Adventure Works
- data [Visual Studio], sample databases
- sample databases, Northwind
- Northwind sample database
- Adventure Works sample database
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fd51bd397e6db3728c10f52db68d45e226fb605b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251047"
---
# <a name="how-to-install-sample-databases"></a>Практическое руководство. Установка образцов баз данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Многие примеры данных требуют возможности подключения к примерам баз данных Northwind, Pubs и AdventureWorks. Можно установить эти базы данных и подключаться к ним, используя следующие процедуры.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="installing-databases"></a>Установка баз данных  
 Многие примеры данных требуют доступности примеров баз данных, которые можно загрузить с веб-сайтов. К примерам баз данных относятся AdventureWorks, Northwind и Pubs.  
  
#### <a name="to-install-the-northwind-and-pubs-sample-databases-for-sql-server"></a>Установка учебных баз данных "Борей" и Pubs для SQL Server  
  
1.  Перейдите к [Northwind и Pubs образцов баз данных](http://go.microsoft.com/fwlink?linkid=64296) веб-сайта.  
  
2.  Загрузите и запустите установщик.  
  
     Установщик добавляет папку **SQL Server 2000 Sample Databases** в корневую папку на компьютере. (Например: **C:\SQL Server 2000 Sample Databases**).  
  
3.  Найдите скрипт SQL для нужной базы данных (Northwind или Pubs).  
  
    > [!WARNING]
    >  Файл базы данных .MDF невозможно легко преобразовать в формат, который можно использовать в текущих версиях SQL Server, поэтому лучше использовать для создания базы данных скрипт.  
  
4.  В **обозревателя серверов**, создать подключение к экземпляру SQL Server, где требуется установить базу данных. При отсутствии конкретного нужного экземпляра SQL Server можно использовать базу данных, которая автоматически устанавливается с Visual Studio. Чтобы сделать это, укажите `(localdb)\v11.0` как имя сервера.  
  
     Для создания подключения выполните следующие шаги.  
  
    ###### <a name="to-create-a-connection-to-an-instance-of-sql-server"></a>Создание подключения к экземпляру SQL Server  
  
    1.  В **обозревателя серверов**, откройте контекстное меню для **подключения к данным** узел и выберите **добавить подключение**.  
  
         **Добавить подключение** откроется диалоговое окно.  
  
    2.  Введите название экземпляра SQL Server, где необходимо создать базу данных Northwind или Pubs, либо введите (localdb)\v11.0.  
  
    3.  В разделе **выберите или введите имя базы данных**, выберите любую базу данных из списка, например, базы данных tempdb.  
  
    4.  Выберите **проверить подключение** кнопку, чтобы убедиться, что все работает, а затем выберите **ОК** кнопки.  
  
         Новый узел подключения появится в **обозревателя серверов**.  
  
5.  В контекстном меню узла подключения для сервера а затем выберите **новый запрос** кнопки.  
  
     Откроется окно редактора с пустым SQL-файлом скрипта.  
  
6.  Вставьте содержимое файла instnwnd.sql или instpubs.sql в окно редактора.  
  
7.  Нажмите кнопку выполнения запроса (значок в виде открытого зеленого треугольника в верхней правой части окна запроса).  
  
     Если запрос выполнен успешно, сообщение **выполнение команд успешно завершено** отображается. Это означает, что база данных Northwind или Pubs создана.  
  
     Необходимо еще добавить подключение к этой демонстрационной базе данных. В **обозревателя серверов**, откройте контекстное меню для **подключения к данным** узел и выберите **добавить подключение**.  
  
8.  Выберите тот же сервер, который вы выбрали раньше, но на этот раз в списке выберите базы данных или введите имя базы данных, выберите базу данных Northwind или pubs и выберите **ОК** кнопки.  
  
     В разделе подключений к данным появится новый узел для демонстрационной базы данных.  
  
9. Закройте окно редактора и подтвердите, что файл запроса сохранять не нужно. После создания базы данных скрипт для создания базы данных сохранять не требуется.  
  
#### <a name="to-install-the-adventureworks-sample-databases"></a>Чтобы установить учебные базы данных AdventureWorks  
  
-   Образцы баз данных AdventureWorks из [веб-сайте CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
#### <a name="to-install-the-northwind-sample-database-for-microsoft-access"></a>Установка учебной базы данных "Борей" для Microsoft Access  
  
1.  В Microsoft Access 2010 или более поздней версии, найдите шаблоны в Интернете "Борей" и выберите **образца базы данных Desktop Northwind 2007**.  
  
2.  В Microsoft Access сохраните файл базы данных с именем Northwind.accdb.  
  
 Новое расширение для баз данных Access — ACCDB. См. в разделе [программирование данных с помощью Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx). Чтобы подключиться к базе данных "Борей" с помощью Access, см. в разделе [как: подключение к базе данных "Борей"](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Примеры баз данных приводятся только для иллюстрации и не обязательно демонстрируют лучшие методики обеспечения безопасности.  
  
## <a name="see-also"></a>См. также  
 [Как определить версию и выпуск SQL Server и ее компонентов](http://support.microsoft.com/kb/321185)   
 [Создание базы данных SQL с помощью конструктора](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [Практическое руководство. Подключение к базе данных "Борей"](../data-tools/how-to-connect-to-the-northwind-database.md)