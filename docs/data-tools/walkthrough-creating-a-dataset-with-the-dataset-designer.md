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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f91c24885cc6817889671dd7a1a6e7e1686ce93f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565004"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Пошаговое руководство. Создание набора данных с помощью конструктора наборов данных

В этом пошаговом руководстве, создать набор данных с помощью **конструктор наборов данных**. Статьи описан процесс создания нового проекта и добавления нового **набора данных** элемента к нему. Вы узнаете о создании таблиц, основанных на таблицах в базе данных без использования мастера.

## <a name="prerequisites"></a>Предварительные требования

В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.

1. Если у вас нет SQL Server Express LocalDB, установите его из [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. В установщике Visual Studio, SQL Server Express LocalDB можно установить как часть **хранение и обработка данных** рабочей нагрузки, или в качестве отдельного компонента.

2. Установка образца базы данных "Борей", выполнив следующие действия:

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранение и обработка данных** рабочей нагрузки в установщике Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на локальном экземпляре LocalDB и выберите **новый запрос**.

       Откроется окно редактора запросов.

    2. Копировать [скрипт Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных "Борей" с нуля и заполняет ее данными.

    3. Вставьте сценарий T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.

       Через некоторое время завершения выполнения запроса и создания базы данных Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Создание проекта приложения Windows Forms

1. В Visual Studio на **файл** меню, выберите **New** > **проекта**.

2. Разверните **Visual C#** или **Visual Basic** левой панели, а затем выберите **Windows Desktop**.

3. В средней области выберите **приложения Windows Forms** тип проекта.

4. Назовите проект **DatasetDesignerWalkthrough**, а затем выберите **ОК**.

     Visual Studio добавит проект в **обозревателе решений** и отобразить новую форму в конструкторе.

## <a name="add-a-new-dataset-to-the-application"></a>Добавить новый набор данных в приложение

1. В меню **Проект** выберите пункт **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

2. В области слева выберите **данных**, а затем выберите **набора данных** в средней области.

3. Имя набора данных **NorthwindDataset**, а затем выберите **добавить**.

     Visual Studio добавляет в файл с именем **NorthwindDataset.xsd** в проект и открывает его в **конструктор наборов данных**.

## <a name="create-a-data-connection-in-server-explorer"></a>Создание подключения к данным в обозревателе сервера

1. В меню **Вид** выберите **Обозреватель сервера**.

2. В **обозревателя серверов**, нажмите кнопку **подключение к базе данных** кнопки.

3. Создайте подключение к базе данных Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Создать таблицы в наборе данных

В этом разделе описывается добавление таблиц в наборе данных.

### <a name="to-create-the-customers-table"></a>Чтобы создать таблицу Customers

1. Разверните узел соединения данных, созданную в **обозревателя серверов**и затем разверните **таблиц** узла.

2. Перетащите **клиентов** таблицу **обозревателя серверов** на **конструктор наборов данных**.

     Объект **клиентов** таблицы данных и **CustomersTableAdapter** добавляются в набор данных.

### <a name="to-create-the-orders-table"></a>Чтобы создать таблицу Orders

- Перетащите **заказы** таблицу **обозревателя серверов** на **конструктор наборов данных**.

     **Заказы** таблицы данных, **OrdersTableAdapter**и связь между данными **клиентов** и **заказы** таблицы добавляются набор данных.

### <a name="to-create-the-orderdetails-table"></a>Чтобы создать таблицу OrderDetails

- Перетащите **Order Details** таблицу **обозревателя серверов** на **конструктор наборов данных**.

     **Order Details** таблицы данных, **OrderDetailsTableAdapter**и связь между данными **заказы** и **OrderDetails** таблиц добавляются в набор данных.

## <a name="next-steps"></a>Следующие шаги

- Сохраните набор данных.

- Выберите элементы из **источников данных** окно и перетащите их на форму. Дополнительные сведения см. в разделе [управляет привязки Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Добавьте дополнительные запросы для объектов TableAdapter.

- Добавьте логику проверки <xref:System.Data.DataTable.ColumnChanging> или <xref:System.Data.DataTable.RowChanging> событий таблиц данных в наборе данных. Дополнительные сведения см. в разделе [проверки данных в наборах данных](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>См. также

- [Создание и настройка наборов данных в Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Проверка данных](../data-tools/validate-data-in-datasets.md)