---
title: Сохранение данных с помощью методов DBDirect адаптера таблицы TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 88590c49938ef61344a1092dffb42565a81755d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920145"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Сохранение данных с помощью методов DBDirect адаптера таблицы TableAdapter

В этом пошаговом руководстве приведены подробные инструкции для выполнения инструкций SQL непосредственно к базе данных с помощью методов DBDirect адаптера таблицы. Методы DBDirect адаптера таблицы обеспечивают точный контроль над обновлениями базы данных. Их можно использовать для выполнения определенных инструкций SQL и хранимые процедуры, вызывая отдельные `Insert`, `Update`, и `Delete` методы, необходимые для приложения (в отличие от перегруженного `Update` метод, который выполняет обновление INSERT и инструкций DELETE в одном вызове).

В этом пошаговом руководстве описаны следующие процедуры.

-   Создание **приложения Windows Forms**.

-   Создание и настройка набора данных с помощью [мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png).

-   Выбор элемента управления, создаваемого на форме при перетаскивании элементов из окна **Источники данных**. Дополнительные сведения см. в разделе [задать для элемента управления создается при перетаскивании из окна источников данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Создание формы с привязкой к данным посредством перетаскивания элементов из окна **Источники данных** на форму.

-   Добавьте методы для непосредственного доступа к базе данных, выполнения операций вставки, обновления и удаления.

## <a name="prerequisites"></a>Предварительные требования

В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.

1. Если у вас нет SQL Server Express LocalDB, установите его из [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. В **установщик Visual Studio**, можно установить SQL Server Express LocalDB как часть **хранение и обработка данных** рабочей нагрузки, или в качестве отдельного компонента.

2. Установка образца базы данных "Борей", выполнив следующие действия:

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

4. Назовите проект **TableAdapterDbDirectMethodsWalkthrough**, а затем выберите **ОК**.

     Создается проект **TableAdapterDbDirectMethodsWalkthrough**, который добавляется в **Обозреватель решений**.

## <a name="create-a-data-source-from-your-database"></a>Создать источник данных из базы данных

В этом шаге **Мастер настройки источника данных** используется для создания источника данных на основе таблицы `Region` в учебной базе данных "Борей". Для создания подключения необходимо иметь доступ к учебной базе данных "Борей". Сведения о настройке учебной базе данных Northwind, см. в разделе [как: Установка образцов баз данных](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>Создание источника данных

1. На **данных** меню, выберите **Показать источники данных**.

   Открывается окно **Источники данных**.

2. В окне **Источники данных** выберите **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.

3. На **Выбор типа источника данных** выберите **базы данных**, а затем выберите **Далее**.

4. На **Выбор подключения базы данных** экрана, выполните одно из следующих:

    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

         - или -

    -   Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение**.

5. Если для базы данных требуется пароль, выберите параметр для включения конфиденциальных данных, а затем выберите **Далее**.

6. На **сохранение подключения в файле конфигурации приложения** выберите **Далее**.

7. На **Выбор объектов базы данных** экрана, разверните узел **таблиц** узла.

8. Выберите `Region` таблицы, а затем выберите **Готово**.

     Объект **NorthwindDataSet** добавляется в проект, и таблица `Region` отображается в окне **Источники данных**.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Добавление элементов управления в форму для отображения данных

Создайте элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.

Чтобы создать элементы управления с привязкой к данным на форме Windows, перетащите главный **регион** узел из **источников данных** окна в форму.

На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Порядок добавления кнопок, вызывающих отдельные методы DbDirect адаптера таблицы

1. Перетащите три элемента управления <xref:System.Windows.Forms.Button> из **области элементов** на **Form1** (под **RegionDataGridView**).

2. Задайте следующие свойства **Имя** и **Текст** для каждой из кнопок.

    |name|Text|
    |----------|----------|
    |`InsertButton`|**Вставить**|
    |`UpdateButton`|**Обновление**|
    |`DeleteButton`|**Удалить**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Добавление кода для вставки новых записей в базу данных

1. Выберите **InsertButton** создайте обработчик событий для события click и открыть форму в редакторе кода.

2. Замените обработчик событий `InsertButton_Click` следующим кодом:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Добавление кода для обновления записей в базе данных

1. Дважды щелкните **UpdateButton**, чтобы создать обработчик событий для события щелчка кнопкой мыши и открыть форму в редакторе кода.

2. Замените обработчик событий `UpdateButton_Click` следующим кодом:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>Чтобы добавить код для удаления записей из базы данных

1. Выберите **DeleteButton** создайте обработчик событий для события click и открыть форму в редакторе кода.

2. Замените обработчик событий `DeleteButton_Click` следующим кодом:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Запуск приложения

-   Выберите **F5** для запуска приложения.

-   Выберите **вставить** и убедитесь, что новая запись отображается в сетке.

-   Выберите **обновления** и убедитесь, что запись обновляется в сетке.

-   Выберите **удалить** и убедитесь, что запись удаляется из сетки.

## <a name="next-steps"></a>Следующие шаги

В зависимости от требований приложения существуют несколько шагов, которые может потребоваться выполнить после создания формы с привязкой к данным. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.

-   Добавление функциональности поиска в форму.

-   Добавление дополнительных таблиц в набор данных посредством выбора элемента **Настроить набор данных с помощью мастера** в окне **Источники данных**. Вы можете добавить элементы управления, отображающие связанные данные, перетащив связанные узлы на форму. Дополнительные сведения см. в разделе [отношения в наборах данных](relationships-in-datasets.md).

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)