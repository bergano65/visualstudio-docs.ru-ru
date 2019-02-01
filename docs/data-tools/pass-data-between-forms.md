---
title: Передача данных между формами
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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 6d4e7d85892974b1ef2d4600525b37c45c7ac8fa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946182"
---
# <a name="pass-data-between-forms"></a>Передача данных между формами

Это пошаговое руководство содержит инструкции по передаче данных из одной формы в другую. Использование таблиц customers и orders из Northwind, одна форма позволяет пользователям выбрать клиента и второй форме отображаются заказы выбранного клиента. В этом пошаговом руководстве показано, как создать метод на второй форме, которая получает данные из первой формы.

> [!NOTE]
> Здесь демонстрируется всего один способ передачи данных между формами. Существуют другие способы передать данные в форму, включая создание второй конструктор для получения данных, или создание общедоступного свойства, которое можно задать с помощью данных из первой формы.

В данном пошаговом руководстве представлены следующие задачи.

-   Создание нового **приложение Windows Forms** проекта.

-   Создание и настройка набора данных с помощью [мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png).

-   Выбор элемента управления, создаваемого на форме при перетаскивании элементов из окна **Источники данных**. Дополнительные сведения см. в разделе [задать для элемента управления создается при перетаскивании из окна источников данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Создание элемента управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.

-   Создание второй формы с сеткой для отображения данных.

-   Создание запроса адаптера таблицы для получения заказов определенного клиента.

-   Передача данных между формами.

## <a name="prerequisites"></a>Предварительные требования

В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.

1.  Если у вас нет SQL Server Express LocalDB, установите его из [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. В установщике Visual Studio, SQL Server Express LocalDB можно установить как часть **хранение и обработка данных** рабочей нагрузки, или в качестве отдельного компонента.

2.  Установка образца базы данных "Борей", выполнив следующие действия:

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранение и обработка данных** рабочей нагрузки в установщике Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на локальном экземпляре LocalDB и выберите **новый запрос**.

       Откроется окно редактора запросов.

    2. Копировать [скрипт Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных "Борей" с нуля и заполняет ее данными.

    3. Вставьте сценарий T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.

       Через некоторое время выполнения запроса отобразятся и создания базы данных Northwind.

## <a name="create-the-windows-forms-app-project"></a>Создайте проект приложения Windows Forms

1. В Visual Studio на **файл** меню, выберите **New** > **проекта**.

2. Разверните **Visual C#**  или **Visual Basic** левой панели, а затем выберите **Windows Desktop**.

3. В средней области выберите **приложения Windows Forms** тип проекта.

4. Назовите проект **PassingDataBetweenForms**, а затем выберите **ОК**.

     Создается проект **PassingDataBetweenForms**, который добавляется в **Обозреватель решений**.

## <a name="create-the-data-source"></a>Создание источника данных

1.  Чтобы открыть **источников данных** окна на **данных** меню, щелкните **Показать источники данных**.

2.  В окне **Источники данных** выберите **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.

3.  На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.

4.  На странице **Выбор модели базы данных** выберите **Набор данных** и нажмите кнопку **Далее**.

5.  На странице **Выбор подключения к базе данных** выполните одно из следующих действий:

    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

    -   Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение**.

6.  Если базе данных требуется пароль и выбран параметр для включения конфиденциальных данных, выберите параметр и нажмите кнопку **Далее**.

7.  На **сохранение подключения в файле конфигурации приложения** щелкните **Далее**.

8.  Разверните узел **Таблицы** на странице **Выбор объектов базы данных**.

9. Выберите таблицы **Customers** и **Orders** и нажмите кнопку **Готово**.

     **NorthwindDataSet** добавляется в проект, и таблицы **Customers** и **Orders** отображаются в окне **Источники данных**.

## <a name="create-the-first-form-form1"></a>Создание первой формы (Form1)

Вы можете создать сетку с привязкой к данным (элемент управления <xref:System.Windows.Forms.DataGridView>) с помощью перетаскивания узла **Customers** из окна **Источники данных** на форму.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Создание сетки с привязкой к данным на форме

-   Перетащите главный узел **Customers** из окна **Источники данных** на форму **Form1**.

     На форме **Form1** появляется <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. В области компонентов появляется [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> и <xref:System.Windows.Forms.BindingNavigator>.

## <a name="create-the-second-form"></a>Создание второй формы

Создание второй формы для передачи данных.

1.  В меню **Проект** выберите пункт **Добавить форму Windows**.

2.  Оставьте имя по умолчанию **Form2** и нажмите кнопку **Добавить**.

3.  Перетащите главный узел **Orders** из окна **Источники данных** на форму **Form2**.

     На форме **Form2** появляется <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. В области компонентов появляется [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> и <xref:System.Windows.Forms.BindingNavigator>.

4.  Удалите **OrdersBindingNavigator** из области компонентов.

     **OrdersBindingNavigator** исчезает из **Form2**.

## <a name="add-a-tableadapter-query"></a>Добавление запроса адаптера таблицы

Добавление запроса адаптера таблицы на форму Form2 для загрузки заказов выбранного клиента на форме Form1.

1.  Дважды щелкните файл **NorthwindDataSet.xsd** в **обозревателе решений**.

2.  Щелкните правой кнопкой мыши элемент **OrdersTableAdapter** и выберите пункт **Добавить запрос**.

3.  Оставьте параметр по умолчанию **Использовать инструкции SQL** и нажмите кнопку **Далее**.

4.  Оставьте параметр по умолчанию **Инструкция SELECT, возвращающая строки** и нажмите кнопку **Далее**.

5.  Добавьте в запрос предложение WHERE, чтобы возвратить `Orders` на основании `CustomerID`. Запрос должен выглядеть примерно следующим образом:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Проверьте правильность синтаксиса параметров для своей базы данных. Например, в Microsoft Access предложение WHERE должно выглядеть следующим образом: `WHERE CustomerID = ?`.

6.  Нажмите кнопку **Далее**.

7.  Для **заполнения имя DataTableMethod**, тип `FillByCustomerID`.

8.  Снимите флажок **Вернуть таблицу данных (DataTable)** и нажмите кнопку **Далее**.

9. Нажмите кнопку **Готово**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Создание метода на форме Form2 для передачи данных

1.  Щелкните правой кнопкой мыши **Form2** и выберите пункт **Просмотреть код**, чтобы открыть **Form2** в **редакторе кода**.

2.  Добавьте следующий код в **Form2** после метода `Form2_Load`:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Создание метода на форме Form1 для передачи данных и отображения Form2

1.  В **Form1** щелкните правой кнопкой мыши сетку данных клиентов и выберите пункт **Свойства**.

2.  В окне **Свойства** выберите **События**.

3.  Дважды щелкните событие **CellDoubleClick**.

     Откроется окно редактора кода.

4.  Обновите определение метода в соответствии со следующим примером:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Запуск приложения

-   Нажмите клавишу **F5** для запуска приложения.

-   Дважды щелкните запись клиента в форме **Form1**, чтобы открыть **Form2** с заказами этого клиента.

## <a name="next-steps"></a>Следующие шаги

В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после передачи данных между формами. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.

-   Изменение набора данных для добавления или удаления объектов базы данных. Дополнительные сведения см. в разделе, посвященном [созданию и настройке наборов данных](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Добавление функциональности для сохранения данных в базу данных. Дополнительные сведения см. в разделе [сохранить данные в базе данных](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>См. также

- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)