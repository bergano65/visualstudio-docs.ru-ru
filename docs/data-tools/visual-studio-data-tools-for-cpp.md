---
title: "Данные средства Visual Studio для C++ | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CPP
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 0b7f49708c00bd02fb8c74bc3ed6258d41729bf2
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="visual-studio-data-tools-for-c"></a>Данные средства Visual Studio для C++

Для машинного кода C++ обеспечивают максимальную производительность при получении доступа к источникам данных. Однако данные, для приложений C++ в Visual Studio для работы с проектами не столь широки, как и для приложений .NET. Например windows источники данных не может использоваться для источников данных в рабочую область конструирования C++ перетаскивание. При необходимости объектно реляционного слоя будет написать собственный, или используйте продуктов независимых производителей.  То же верно и для функции привязки данных, несмотря на то, что приложения, использующие библиотеку Microsoft Foundation Class можно использовать некоторые классы баз данных вместе с документами и представлениями, для хранения данных в памяти и его отображения для пользователя. Дополнительные сведения см. в разделе [доступ к данным в Visual C++](/cpp/data/data-access-in-cpp).

Чтобы подключиться к базам данных SQL, приложений C++ неуправляемого кода можно использовать драйверы ODBC и OLE DB и ADO поставщика, который входит в состав Windows. Их можно подключиться к любой базе данных, которая поддерживает эти интерфейсы. Драйвер ODBC является стандартным. OLE DB предоставляется для обеспечения обратной совместимости. Дополнительные сведения об этих технологий данных см. в разделе [компоненты доступа к данным Windows](https://msdn.microsoft.com/library/windows/desktop/aa968814.aspx).

Чтобы воспользоваться преимуществами пользовательских функций в SQL Server 2005 и более поздней версии, используйте [собственный клиент SQL Server](/sql/relational-databases/native-client/sql-server-native-client). Собственный клиент также содержит, драйвер ODBC для SQL Server и поставщика SQL Server OLE DB в одну собственную динамическую библиотеку (DLL). Они поддерживают приложения, использующие API машинного кода (ODBC, OLE DB и ADO) для Microsoft SQL Server.  Собственный клиент SQL Server устанавливается вместе с SQL Server Data Tools. Руководство по программированию находится здесь: [программирование SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Подключение к localDB через ODBC и собственный клиент SQL из приложения C++  
  
1.  Установка SQL Server Data Tools.  
  
2.  Если требуется образец базы данных SQL для подключения к загрузить базу данных Northwind и распакуйте его на новое место.  
  
3.  Используйте SQL Server Management Studio для присоединения к localDB распаковать файл Northwind.mdf. При запуске SQL Server Management Studio подключитесь к (localdb) \MSSQLLocalDB.  
  
     ![Диалоговое окно подключения SSMS](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS подключения диалогового окна")  
  
     Нажмите правой кнопкой мыши узел localdb на левой панели и выберите **присоединение**.  
  
     ![Среда SSMS присоединение базы данных](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS присоединение базы данных")  
  
4.  Загрузите пример Windows SDK ODBC и распакуйте его на новое место. Этот пример показывает основные команды ODBC, которые используются для подключения к базе данных и отправлять запросы и команды. Дополнительные сведения об этих функциях в [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). При первой загрузке решения (он находится в папке C++), Visual Studio предложит обновление решения до текущей версии Visual Studio. Нажмите кнопку **Да**.
  
5.  Чтобы использовать собственный клиент, необходимо его файлом заголовка и lib-файл. Эти файлы содержат функции и специальные определения для SQL Server за пределами функции ODBC, определенные в sql.h. В **проекта** > **свойства** > **каталоги VC ++**, добавьте каталог включаемых следующее:

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

И этот каталог библиотеки:

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6.  Добавьте следующие строки в odbcsql.cpp. #Define предотвращает играет определений OLE DB из компиляции.  
  
    ```cpp
    #define _SQLNCLI_ODBC_  
    #include <sqlncli.h>  
    ```  
  
    Обратите внимание, что образец не использует возможности собственного клиента, описанные выше шаги не обязательны для того, чтобы скомпилировать и запустить. Но теперь проект настроен для использования этой функции. Дополнительные сведения см. в разделе [программирование SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client).  
  
7.  Укажите, какой драйвер следует использовать в подсистеме ODBC. Образец передает атрибут строки подключения ДРАЙВЕРА в качестве аргумента командной строки. В **проекта** > **свойства** > **Отладка**, добавьте следующий аргумент команды:  
  
    ```cpp
    DRIVER="SQL Server Native Client 11.0"  
    ```  
  
8.  Нажмите клавишу F5, чтобы выполнить сборку приложения и запустить его. Вы увидите диалоговое окно драйвера, необходимо ввести базы данных. Введите `(localdb)\MSSQLLocalDB`и проверьте **использовать доверительное соединение**. Press **OK**. Вы увидите консоли с сообщениями, которые указывают на успешное подключение. Вы также увидите командную строку для ввода в инструкции SQL. На следующем рисунке показано пример запроса и результатов:  
  
     ![Пример ODBC выходных данных запроса](../data-tools/media/raddata-odbc-sample-query-output.png "raddata выходных данных запроса пример ODBC")  
  
## <a name="see-also"></a>См. также

[Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)