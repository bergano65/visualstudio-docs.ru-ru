---
title: Visual Studio Data Tools для C++ | Документация Майкрософт
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: ec68d54ced85737d66c64ca2dbf7942ca81e5314
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621209"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio Data Tools для C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Собственный C++ часто может обеспечить максимальную производительность при доступе к источникам данных. Однако средства для данных приложений C++ в Visual Studio не так обширны, как для приложений .NET. Например, окна источников данных нельзя использовать для перетаскивания источников данных на поверхность проектирования C++. Если вам нужен объектно-реляционный слой, вам придется написать собственный или использовать сторонний продукт.  Это справедливо и для функций привязки данных, хотя приложения, использующие библиотеку классов Microsoft Foundation, могут использовать некоторые классы баз данных вместе с документами и представлениями, чтобы хранить данные в памяти и отображать их для пользователя. Дополнительные сведения см. [в разделе доступ к данным в Visual C++](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .

 Для подключения к базам данных SQL собственные приложения C++ могут использовать драйверы ODBC и OLE DB и поставщик ADO, входящий в состав Windows.     Они могут подключаться к любой базе данных, которая поддерживает эти интерфейсы. Драйвер ODBC является стандартным. OLE DB предоставляется для обеспечения обратной совместимости. Дополнительные сведения об этих технологиях данных см. в разделе [Компоненты доступа к данным Windows](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx) .

 Чтобы воспользоваться преимуществами пользовательских функций в SQL Server 2005 и более поздних версиях, используйте [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Собственный клиент также содержит драйвер SQL Server ODBC и поставщик SQL Server OLE DB в одной собственной библиотеке динамической компоновки (DLL). Они поддерживают приложения, использующие интерфейсы API машинного кода (ODBC, OLE DB и ADO) для Microsoft SQL Server.  SQL Server Native Client устанавливается вместе с SQL Server Data Tools. Руководство по программированию: [SQL Server Native Client программирование](https://msdn.microsoft.com/library/ms130892.aspx).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Подключение к localDB через ODBC и SQL Native Client из приложения C++

1. Установите SQL Server Data Tools.

2. Если вам нужен образец базы данных SQL для подключения, скачайте базу данных Northwind и распакуйте ее в новое расположение.

3. Используйте SQL Server Management Studio, чтобы подключить Распакованный MDF-файл Northwind к localDB. При запуске SQL Server Management Studio подключение к (LocalDB) \Мсскллокалдб.

    ![Диалоговое окно подключения SSMS](../data-tools/media/raddata-ssms-connect-dialog.png "диалоговое окно подключения SSMS раддата")

    Затем щелкните правой кнопкой мыши узел LocalDB на левой панели и выберите команду **присоединить**.

    ![Присоединение базы данных SSMS](../data-tools/media/raddata-ssms-attach-database.png "Присоединение базы данных раддата SSMS")

4. Скачайте пример Windows SDK ODBC и распакуйте его в новое расположение. В этом примере показаны основные команды ODBC, которые используются для подключения к базе данных и выдаются запросы и команды. Дополнительные сведения об этих функциях см. в статье [Microsoft Open Database Connectivity (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). При первой загрузке решения (оно находится в папке C++) Visual Studio предложит обновить решение до текущей версии Visual Studio. Нажмите кнопку **Да**.

5. Для использования собственного клиента требуется файл заголовка и файл LIB. Эти файлы содержат функции и определения, характерные для SQL Server, помимо функций ODBC, определенных в SQL. h. В **Project**  >  **свойствах**проекта  >  **каталоги VC + +** добавьте следующий каталог include:

   ** \<system drive> : \PROGRAM Files\Microsoft SQL Server\110\SDK\Include** и этот каталог библиотеки:

   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**

6. Добавьте эти строки в одбкскл. cpp. #Define предотвращает компиляцию незначимых OLE DB определений.

   ```
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Обратите внимание, что в этом примере не используются функции собственного клиента, поэтому для компиляции и выполнения описанные выше действия не требуются. Но теперь проект настроен для использования этой функции. Дополнительные сведения см. в статье [Программирование SQL Server Native Client](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).

7. Укажите, какой драйвер следует использовать в подсистеме ODBC. Образец передает атрибут строки подключения драйвера в в качестве аргумента командной строки. В **Project**окне  >  **Properties**  >  **Отладка**свойств проекта добавьте следующий аргумент команды:

   ```
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Нажмите клавишу F5, чтобы создать и запустить приложение. Появится диалоговое окно с драйвером, предлагающим ввести базу данных. Введите `(localdb)\MSSQLLocalDB` и установите флажок **использовать доверительное соединение**. Нажмите кнопку **ОК**. Вы увидите консоль с сообщениями, которые указывают на успешное соединение. Кроме того, должна отобразиться Командная строка, в которой можно ввести инструкцию SQL. На следующем экране показан пример запроса и результаты.

    ![Пример выходных данных запроса ODBC](../data-tools/media/raddata-odbc-sample-query-output.png "вывод примера запроса раддата ODBC")

## <a name="see-also"></a>См. также:
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
