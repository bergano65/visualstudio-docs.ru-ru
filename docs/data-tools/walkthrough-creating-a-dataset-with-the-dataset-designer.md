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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: dbf84a236dfee809b1cccac7627106f32da2a696
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Пошаговое руководство. Создание набора данных с помощью конструктора наборов данных

В этом пошаговом руководстве будет создан набор данных с помощью **конструктора наборов данных**. Он поможет выполнить процесс создания нового проекта и добавления нового **DataSet** элемента к нему. Вы узнаете, как создавать таблицы, на основе таблиц в базе данных без использования мастера.

В данном пошаговом руководстве представлены следующие задачи.

-   Создание нового **приложение Windows Forms** проекта.

-   Добавление пустой **DataSet** в проект.

-   Создание и настройка источника данных в приложении путем создания набора данных с **конструктора наборов данных**.

-   Создание подключения к базе данных Northwind в **обозревателя серверов**.

-   Создание таблиц с помощью адаптеров таблиц в наборе данных, основанных на таблицах в базе данных.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Предварительные требования
В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.

1.  Если у вас нет SQL Server Express LocalDB, установите его из [страницы загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. Установщик Visual Studio можно установить SQL Server Express LocalDB в рамках **хранения и обработки данных** рабочей нагрузки, или в отдельных компонентов.

2.  Установка образца базы данных Northwind, выполните следующие действия:

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранения и обработки данных** рабочей нагрузки в установщик Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на экземпляре LocalDB и выберите **нового запроса...** .

       Откроется окно редактора запросов.

    2. Копировать [сценарий Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот скрипт T-SQL создает базу данных Northwind с нуля и заполняет ее данными.

    3. Вставьте скрипт T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.

       Через некоторое время завершения выполнения запроса и создания базы данных "Борей".

## <a name="creating-a-new-windows-forms-application-project"></a>Создание нового проекта приложения Windows Forms

#### <a name="to-create-a-new-windows-forms-application-project"></a>Для создания нового проекта приложения Windows Forms

1. В Visual Studio на **файл** последовательно выберите пункты **New**, **проекта...** .

2. Разверните **Visual C#** или **Visual Basic** на левой панели, затем выберите **классического Windows**.

3. В средней области выберите **приложение Windows Forms** тип проекта.

4. Назовите проект **DatasetDesignerWalkthrough**, а затем выберите **ОК**.

     Visual Studio добавляет проект в **обозревателе решений** и отобразит новую форму в конструкторе.

## <a name="adding-a-new-dataset-to-the-application"></a>Добавление нового набора данных в приложение

#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Чтобы добавить новый элемент набора данных в проект

1.  На **проекта** последовательно выберите пункты **добавить новый элемент...** .

     Откроется диалоговое окно **Добавление нового элемента**.

2.  На левой панели выберите **данные**, а затем выберите **DataSet** в средней области.

3.  Имя набора данных **NorthwindDataset**, а затем выберите **добавить**.

     Visual Studio добавляет файл с именем **NorthwindDataset.xsd** в проект и открывает его в **конструктора наборов данных**.

## <a name="creating-a-data-connection-in-server-explorer"></a>Создание подключения к данным в обозревателе серверов

#### <a name="to-create-a-connection-to-the-northwind-database"></a>Чтобы создать подключение к базе данных Northwind

1.  На **представление** меню, нажмите кнопку **обозревателя серверов**.

2.  В **обозревателя серверов**, нажмите кнопку **подключение к базе данных** кнопки.

3.  Создайте подключение к учебной базе данных "Борей".

## <a name="creating-the-tables-in-the-dataset"></a>Создание таблиц в наборе данных
В этом разделе описывается добавление таблиц в наборе данных.

#### <a name="to-create-the-customers-table"></a>Чтобы создать таблицу Customers

1.  Разверните подключение данных, созданных в **обозревателя серверов**, а затем разверните **таблиц** узла.

2.  Перетащите **клиентов** таблицу **обозревателя серверов** на **конструктора наборов данных**.

     Объект **клиентов** таблицы данных и **CustomersTableAdapter** добавляются в набор данных.

#### <a name="to-create-the-orders-table"></a>Чтобы создать таблицу Orders

-   Перетащите **заказов** таблицу **обозревателя серверов** на **конструктора наборов данных**.

     **Заказов** таблицы данных **OrdersTableAdapter**и связь между данными **клиентов** и **заказов** таблицы добавляются набор данных.

#### <a name="to-create-the-orderdetails-table"></a>Чтобы создать таблицу OrderDetails

-   Перетащите **Order Details** таблицу **обозревателя серверов** на **конструктора наборов данных**.

     **Order Details** таблицы данных **OrderDetailsTableAdapter**и связь между данными **заказов** и **OrderDetails** таблиц добавляются в набор данных.

## <a name="next-steps"></a>Следующие шаги

### <a name="to-add-functionality-to-your-application"></a>Добавление функциональности в приложение

-   Сохраните набор данных.

-   Выберите элементы в **источники данных** окна и перетащите их на форму. Дополнительные сведения см. в разделе [элементы управления Windows Forms, привязка к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

-   Добавьте дополнительные запросы адаптеров таблиц.

-   Добавьте логику проверки в <xref:System.Data.DataTable.ColumnChanging> или <xref:System.Data.DataTable.RowChanging> событий таблиц данных в наборе данных. Дополнительные сведения см. в разделе [проверка данных в наборах данных](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>См. также

- [Создание и настройка наборов данных в Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Проверка данных](../data-tools/validate-data-in-datasets.md)
- [Сохранение данных](../data-tools/saving-data.md)