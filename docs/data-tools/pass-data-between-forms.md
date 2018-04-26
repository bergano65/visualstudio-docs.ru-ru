---
title: Передачи данных между формами
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4b8a1865dc6fce56f11faa453a4786ae799af7e3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="pass-data-between-forms"></a>Передачи данных между формами
Это пошаговое руководство содержит инструкции по передаче данных из одной формы в другую. С помощью таблиц customers и orders из Northwind, одна форма позволяет пользователям выбрать клиента, а второй форме отображаются заказы выбранного клиента. В этом пошаговом руководстве демонстрируется создание метода на вторую форму, которая получает данные из первой формы.

> [!NOTE]
>  Здесь демонстрируется всего один способ передачи данных между формами. Существуют другие способы передать данные в форму, включая создание второй конструктор для приема данных, или создание открытые свойства, которое можно задать данные из первой формы.

 В данном пошаговом руководстве представлены следующие задачи.

-   Создание нового **приложение Windows Forms** проекта.

-   Создание и настройка набора данных с [мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png).

-   Выбор элемента управления, создаваемого на форме при перетаскивании элементов из **источники данных** окна. Дополнительные сведения см. в разделе [задать элемент управления, создаваемого при перетаскивании из окна источников данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Создание элемента управления с привязкой к данным путем перетаскивания элементов из **источники данных** окна в форму.

-   Создание второй формы с сеткой для отображения данных.

-   Создание запроса адаптера таблицы для получения заказов определенного клиента.

-   Передача данных между формами.

## <a name="prerequisites"></a>Предварительные требования
В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.

1.  Если у вас нет SQL Server Express LocalDB, установите его из [страницы загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. Установщик Visual Studio можно установить SQL Server Express LocalDB в рамках **хранения и обработки данных** рабочей нагрузки, или в отдельных компонентов.

2.  Установка образца базы данных Northwind, выполните следующие действия:

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранения и обработки данных** рабочей нагрузки в установщик Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на экземпляре LocalDB и выберите **нового запроса...** .

       Откроется окно редактора запросов.

    2. Копировать [сценарий Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот скрипт T-SQL создает базу данных Northwind с нуля и заполняет ее данными.

    3. Вставьте скрипт T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.

       Через некоторое время завершения выполнения запроса и создания базы данных "Борей".

## <a name="create-the-windows-forms-application"></a>Создайте приложение Windows Forms

#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows

1. В Visual Studio на **файл** последовательно выберите пункты **New**, **проекта...** .

2. Разверните **Visual C#** или **Visual Basic** на левой панели, затем выберите **классического Windows**.

3. В средней области выберите **приложение Windows Forms** тип проекта.

4. Назовите проект **PassingDataBetweenForms**, а затем выберите **ОК**.

     **PassingDataBetweenForms** создается проект и добавить **обозревателе решений**.

## <a name="create-the-data-source"></a>Создание источника данных

#### <a name="to-create-the-data-source"></a>Создание источника данных

1.  В меню **Данные** выберите команду **Показать источники данных**.

2.  В **источники данных** выберите **добавить новый источник данных** запуск **конфигурации источника данных** мастера.

3.  На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.

4.  На **Выбор модели базы данных** убедитесь, что **Dataset** указано и нажмите кнопку **Далее**.

5.  На **Выбор подключения базы данных** выполните одно из следующих действий:

    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

    -   Выберите **новое подключение** для запуска **Добавить/изменить подключение** диалоговое окно.

6.  Если базе данных требуется пароль и включен параметр для включения конфиденциальных данных, выберите параметр и нажмите кнопку **Далее**.

7.  На **Сохранение строки подключения в файле конфигурации приложения** щелкните **Далее**.

8.  На **Выбор объектов базы данных** разверните **таблиц** узла.

9. Выберите **клиентов** и **заказов** таблицы, а затем щелкните **Готово**.

     **NorthwindDataSet** добавляется в проект и **клиентов** и **заказов** таблицы отображаются в **источники данных** окна.

## <a name="create-the-first-form-form1"></a>Создание первой формы (Form1)
 Можно создать сетку с привязкой к данным ( <xref:System.Windows.Forms.DataGridView> управления), путем перетаскивания **клиентов** узел из **источники данных** на форму.

#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Создание сетки с привязкой к данным на форме

-   Перетащите главный **клиентов** узел из **источники данных** окна на **Form1**.

     Объект <xref:System.Windows.Forms.DataGridView> и полоса инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям отображаются на **Form1**. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.

## <a name="create-the-second-form-form2"></a>Создание второй формы (Form2)

#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Порядок создания второй формы, предназначенной для передачи данных

1.  В меню **Проект** выберите пункт **Добавить форму Windows**.

2.  Оставьте имя по умолчанию **Form2**и нажмите кнопку **добавить**.

3.  Перетащите главный **заказов** узел из **источники данных** окна на **Form2**.

     Объект <xref:System.Windows.Forms.DataGridView> и полоса инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям отображаются на **Form2**. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.

4.  Удалить **OrdersBindingNavigator** из области компонентов.

     **OrdersBindingNavigator** исчезнет из **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Добавление запроса адаптера таблицы в Form2 для загрузки заказов выбранного клиента на форме Form1

#### <a name="to-create-a-tableadapter-query"></a>Для создания запроса адаптера таблицы

1.  Дважды щелкните **NorthwindDataSet.xsd** файла в **обозревателе решений**.

2.  Щелкните правой кнопкой мыши **OrdersTableAdapter**и выберите **добавить запрос**.

3.  Оставьте параметр по умолчанию **использовать инструкции SQL**, а затем нажмите кнопку **Далее**.

4.  Оставьте параметр по умолчанию **SELECT, возвращающая строки**, а затем нажмите кнопку **Далее**.

5.  Добавьте предложение WHERE для запроса, чтобы получить `Orders` на основе `CustomerID`. Запрос должен выглядеть примерно следующим образом:

    ```
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    >  Проверьте правильность синтаксиса параметров для своей базы данных. Например, в Microsoft Access предложение WHERE должно выглядеть следующим образом: `WHERE CustomerID = ?`.

6.  Нажмите кнопку **Далее**.

7.  Для **заполнения имя DataTableMethod**, тип `FillByCustomerID`.

8.  Очистить **вернуть таблицу данных** , а затем щелкните **Далее**.

9. Нажмите кнопку **Готово**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Создание метода на форме Form2 для передачи данных

#### <a name="to-create-a-method-to-pass-data-to"></a>Порядок создания метода, предназначенного для передачи данных

1.  Щелкните правой кнопкой мыши **Form2**и выберите **Просмотр кода** Открытие **Form2** в **редактор кода**.

2.  Добавьте следующий код в **Form2** после `Form2_Load` метод:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Создание метода на форме Form1 для передачи данных и отображения Form2

#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Порядок создания метода, предназначенного для передачи данных в Form2

1.  В **Form1**, щелкните правой кнопкой мыши сетку данных клиентов и нажмите кнопку **свойства**.

2.  В **свойства** окно, нажмите кнопку **события**.

3.  Дважды щелкните **CellDoubleClick** событий.

     Откроется окно редактора кода.

4.  Обновите определение метода в соответствии со следующим примером:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-application"></a>Запуск приложения

#### <a name="to-run-the-application"></a>Запуск приложения

-   Нажмите клавишу F5 для запуска приложения.

-   Дважды щелкните запись клиента в **Form1** Открытие **Form2** с заказов этого клиента.

## <a name="next-steps"></a>Следующие шаги

В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после передачи данных между формами. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.

-   Изменение набора данных для добавления или удаления объектов базы данных. Дополнительные сведения см. в разделе, посвященном [созданию и настройке наборов данных](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Добавление функциональности для сохранения данных в базу данных. Дополнительные сведения см. в разделе [сохранить данные в базе данных](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>См. также

- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)