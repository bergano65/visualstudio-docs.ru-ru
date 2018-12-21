---
title: Пошаговое руководство. Сохранение данных в транзакции
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f9b4fad02b6b0d8324e13d4465f4602c16ce85ba
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305056"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Пошаговое руководство. Сохранение данных в транзакции

В этом пошаговом руководстве демонстрируется сохранение данных в транзакции с помощью <xref:System.Transactions> пространства имен. В этом пошаговом руководстве вы создадите в приложении Windows Forms. Мастер настройки источника данных используется для создания набора данных для двух таблиц в базе данных Northwind. Вы добавите с привязкой к данным элементы управления в форму Windows, а вы измените код BindingNavigator кнопка "Сохранить" для обновления базы данных, в класс TransactionScope.

## <a name="prerequisites"></a>Предварительные требования

В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.

1.  Если у вас нет SQL Server Express LocalDB, установите его из [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. В установщике Visual Studio, SQL Server Express LocalDB можно установить как часть **разработка классических приложений .NET** рабочей нагрузки, или в качестве отдельного компонента.

2.  Установка образца базы данных "Борей", выполнив следующие действия:

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранение и обработка данных** рабочей нагрузки в установщике Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на локальном экземпляре LocalDB и выберите **новый запрос**.

       Откроется окно редактора запросов.

    2. Копировать [скрипт Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных "Борей" с нуля и заполняет ее данными.

    3. Вставьте сценарий T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.

       Через некоторое время выполнения запроса отобразятся и создания базы данных Northwind.

## <a name="create-a-windows-forms-application"></a>Создание приложения Windows Forms

Первым шагом является создание **приложение Windows Forms**.

1. В Visual Studio на **файл** меню, выберите **New** > **проекта**.

2. Разверните **Visual C#**  или **Visual Basic** левой панели, а затем выберите **Windows Desktop**.

3. В средней области выберите **приложения Windows Forms** тип проекта.

4. Назовите проект **SavingDataInATransactionWalkthrough**, а затем выберите **ОК**.

     Создается проект **SavingDataInATransactionWalkthrough**, который добавляется в **Обозреватель решений**.

## <a name="create-a-database-data-source"></a>Создание источника данных базы данных

Этот шаг использует **мастер настройки источника данных** для создания источника данных на основе `Customers` и `Orders` таблиц в базе данных Northwind.

1.  Чтобы открыть **источников данных** окна на **данных** меню, выберите **Показать источники данных**.

2.  В окне **Источники данных** выберите **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.

3.  На **Выбор типа источника данных** выберите **базы данных**, а затем выберите **Далее**.

4.  На **Выбор подключения базы данных** экрана выполните одно из следующих:

    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

         - или -

    -   Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение** и создайте подключение к базе данных "Борей".

5.  Если для базы данных требуется пароль, выберите параметр для включения конфиденциальных данных, а затем выберите **Далее**.

6.  На **сохранение подключения в файле конфигурации приложения** выберите **Далее**.

7.  На **Выбор объектов базы данных** экрана, разверните узел **таблиц** узла.

8.  Выберите `Customers` и `Orders` таблиц, а затем выберите **Готово**.

     Объект **NorthwindDataSet** добавляется в проект, и таблицы `Customers` и `Orders` отображаются в окне **Источники данных**.

## <a name="add-controls-to-the-form"></a>Добавление элементов управления на форму

Вы можете создавать элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.

1. В **источников данных** окне разверните **клиентов** узла.

2. Перетащите главный узел **Customers** из окна **Источники данных** на форму **Form1**.

   На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.

3. Перетащите связанный **заказы** узла (не главный **заказы** узла, но ниже узла связанной дочерней таблицы **факсов** столбец) на форму под  **CustomersDataGridView**.

   На форме появляется <xref:System.Windows.Forms.DataGridView>. `OrdersTableAdapter` И <xref:System.Windows.Forms.BindingSource> отображаются в области компонентов.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Добавьте ссылку на сборку System.Transactions

Транзакции используют пространство имен <xref:System.Transactions>. Ссылка проекта на сборку system.transactions не добавляется по умолчанию, поэтому вам нужно добавить ее вручную.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Порядок добавления ссылки на DLL-файл System.Transactions

1.  На **проекта** меню, выберите **добавить ссылку**.

2.  Выберите **System.Transactions** (на **.NET** вкладку), а затем выберите **ОК**.

     Ссылка на **System.Transactions** добавляется в проект.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Изменение кода в кнопке saveitem объекта BindingNavigator

Для первой таблицы, перетащенной на форму, код добавляется по умолчанию для `click` кнопку событий сохранения <xref:System.Windows.Forms.BindingNavigator>. Для обновления дополнительных таблиц вам необходимо добавить такой код вручную. В этом пошаговом руководстве мы выполнили рефакторинг имеющегося кода сохранения из сохранения обработчик событий нажатия кнопки. Также мы создадим несколько дополнительных методов для предоставления определенной функциональности обновления зависимости от строки должен ли быть добавлены или удалены.

### <a name="to-modify-the-auto-generated-save-code"></a>Изменение автоматически сформированного кода сохранения

1.  Выберите **Сохранить** кнопку **CustomersBindingNavigator** (кнопка со значком гибкого диска).

2.  Замените метод `CustomersBindingNavigatorSaveItem_Click` следующим кодом:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

При согласовании изменений связанных данных применяется следующий порядок.

-   Удалите дочерние записи. (В этом случае удалите записи из `Orders` таблицы.)

-   Удалите родительские записи. (В этом случае удалите записи из `Customers` таблицы.)

-   Вставьте родительские записи. (В данном случае вставьте записи в `Customers` таблицы.)

-   Вставьте дочерние записи. (В данном случае вставьте записи в `Orders` таблицы.)

### <a name="to-delete-existing-orders"></a>Удаление существующих заказов

-   Добавьте следующий метод `DeleteOrders` в **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Удаление существующих клиентов

-   Добавьте следующий метод `DeleteCustomers` в **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Добавление новых клиентов

-   Добавьте следующий метод `AddNewCustomers` в **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Добавление новых заказов

-   Добавьте следующий метод `AddNewOrders` в **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Запуск приложения

Нажмите клавишу **F5** для запуска приложения.

## <a name="see-also"></a>См. также

- [Практическое руководство. Сохранение данных с помощью транзакции](../data-tools/save-data-by-using-a-transaction.md)
- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)