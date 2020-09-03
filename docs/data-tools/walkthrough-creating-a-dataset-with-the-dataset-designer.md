---
title: Пошаговое руководство. Создание набора данных с помощью конструктора наборов данных
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8c525d55de16e859005b9746eb52e5516928b9e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586033"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Пошаговое руководство. Создание набора данных с помощью конструктор наборов данных

В этом пошаговом руководстве вы создадите набор данных с помощью **Конструктор наборов данных**. В этой статье описывается процесс создания нового проекта и добавления в него нового элемента **набора данных** . Вы узнаете, как создавать таблицы на основе таблиц в базе данных без использования мастера.

## <a name="prerequisites"></a>Предварительные требования

В этом пошаговом руководстве используется SQL Server Express LocalDB и образец базы данных Northwind.

1. Если у вас нет SQL Server Express LocalDB, установите его на [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)или с помощью **Visual Studio Installer**. В Visual Studio Installer SQL Server Express LocalDB можно установить как часть рабочей нагрузки **хранения и обработки данных** или как отдельный компонент.

2. Установите учебную базу данных Northwind, выполнив следующие действия.

    1. В Visual Studio откройте окно **Обозреватель объектов SQL Server** . (Обозреватель объектов SQL Server устанавливается как часть рабочей нагрузки **хранения и обработки данных** в Visual Studio Installer.) Разверните узел **SQL Server** . Щелкните правой кнопкой мыши экземпляр LocalDB и выберите **создать запрос**.

       Откроется окно редактора запросов.

    2. Скопируйте [скрипт Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных Northwind с нуля и заполняет ее данными.

    3. Вставьте скрипт T-SQL в редактор запросов, а затем нажмите кнопку **выполнить** .

       По истечении короткого времени выполнение запроса завершается и создается база данных Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Создание проекта приложения Windows Forms

1. В Visual Studio в меню **Файл** выберите пункты **Создать** > **Проект**.

2. В левой области разверните элемент **Visual C#** или **Visual Basic** , а затем выберите пункт **Windows Desktop**.

3. В средней области выберите тип проекта **приложения Windows Forms** .

4. Назовите проект **датасетдесигнервалксраугх**и нажмите кнопку **ОК**.

     Visual Studio добавит проект в **Обозреватель решений** и отобразит новую форму в конструкторе.

## <a name="add-a-new-dataset-to-the-application"></a>Добавление нового набора данных в приложение

1. В меню **Проект** выберите команду **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

2. На панели слева выберите **данные**, а затем выберите **набор данных** в средней области.

3. Присвойте набору данных имя **NorthwindDataSet**и нажмите кнопку **Добавить**.

     Visual Studio добавит файл с именем **NorthwindDataSet. xsd** в проект и откроет его в **Конструктор наборов данных**.

## <a name="create-a-data-connection-in-server-explorer"></a>Создание подключения к данным в обозреватель сервера

1. В меню **Вид** выберите **Обозреватель сервера**.

2. В **Обозреватель сервера**нажмите кнопку **подключиться к базе данных** .

3. Создайте подключение к учебной базе данных Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Создание таблиц в наборе данных

В этом разделе объясняется, как добавить таблицы в набор данных.

### <a name="to-create-the-customers-table"></a>Чтобы создать таблицу Customers

1. Разверните подключение к данным, созданное в **Обозреватель сервера**, а затем разверните узел **таблицы** .

2. Перетащите таблицу **Customers** из **Обозреватель сервера** на **Конструктор наборов данных**.

     Таблица данных **Customers** и **CustomersTableAdapter** добавляются в набор данных.

### <a name="to-create-the-orders-table"></a>Чтобы создать таблицу Orders

- Перетащите таблицу **Orders** из **Обозреватель сервера** на **Конструктор наборов данных**.

     Таблица данных **Orders** , **OrdersTableAdapter**и связь данных между таблицами **Customers** и **Orders** добавляются в набор данных.

### <a name="to-create-the-orderdetails-table"></a>Создание таблицы OrderDetails

- Перетащите таблицу **Order Details** из **Обозреватель сервера** на **Конструктор наборов данных**.

     Таблица данных **Order Details** , **ордердетаилстаблеадаптер**и связь данных между таблицами **Orders** и **OrderDetails** добавляются в набор данных.

## <a name="next-steps"></a>Next Steps

- Сохраните набор данных.

- Выберите элементы в окне **Источники данных** и перетащите их на форму. Дополнительные сведения см. [в разделе привязка Windows Forms элементов управления к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Добавление запросов в TableAdapter.

- Добавьте логику проверки в <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> события или таблиц данных в наборе данных. Дополнительные сведения см. [в разделе Проверка данных в DataSets](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>См. также раздел

- [Создание и настройка наборов данных в Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Проверка данных](../data-tools/validate-data-in-datasets.md)
