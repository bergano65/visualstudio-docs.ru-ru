---
title: "Сохранять данные методы DBDirect адаптера таблицы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 628a3cfc75f786ceb989145ada6e2f2579f349cd
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Сохранять данные методы DBDirect адаптера таблицы
Это пошаговое руководство содержит подробные инструкции для выполнения инструкций SQL непосредственно к базе данных с помощью методов DBDirect адаптера таблицы. Методы DBDirect адаптера таблицы обеспечивают точный контроль над обновлениями базы данных. Их можно использовать для выполнения определенных инструкций SQL и хранимые процедуры, вызывая отдельные `Insert`, `Update`, и `Delete` методы, необходимые для приложения (в отличие от перегруженного `Update` метод, который выполняет обновление INSERT и инструкций DELETE в одном вызове).  
  
 В этом пошаговом руководстве описаны следующие процедуры.  
  
-   Создайте новый **приложение Windows Forms**.  
  
-   Создание и настройка набора данных с [мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Выберите элемент управления, создаваемого на форме при перетаскивании элементов из **источники данных** окна. Дополнительные сведения см. в разделе [задать элемент управления, создаваемого при перетаскивании из окна источников данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Создание формы с привязкой к данным путем перетаскивания элементов из **источники данных** на форму.  
  
-   Добавьте методы для непосредственного доступа к базе данных, выполнения операций вставки, обновления и удаления...  
  
## <a name="prerequisites"></a>Предварительные требования  
В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.  
  
1.  Если у вас нет SQL Server Express LocalDB, установите его из [страницы загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. Установщик Visual Studio можно установить SQL Server Express LocalDB в рамках **хранения и обработки данных** рабочей нагрузки, или в отдельных компонентов.  
  
2.  Установка образца базы данных Northwind, выполните следующие действия:  

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранения и обработки данных** рабочей нагрузки в установщик Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на экземпляре LocalDB и выберите **нового запроса...** .  

       Откроется окно редактора запросов.  

    2. Копировать [сценарий Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот скрипт T-SQL создает базу данных Northwind с нуля и заполняет ее данными.  

    3. Вставьте скрипт T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.  

       Через некоторое время завершения выполнения запроса и создания базы данных "Борей".  
  
## <a name="create-a-windows-forms-application"></a>Создайте приложение Windows Forms  
 Первым шагом является создание **приложение Windows Forms**.  
  
#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows  
  
1. В Visual Studio на **файл** последовательно выберите пункты **New**, **проекта...** .  
  
2. Разверните **Visual C#** или **Visual Basic** на левой панели, затем выберите **классического Windows**.  

3. В средней области выберите **приложение Windows Forms** тип проекта.  

4. Назовите проект **TableAdapterDbDirectMethodsWalkthrough**, а затем выберите **ОК**. 
  
     **TableAdapterDbDirectMethodsWalkthrough** создается и добавляется в проект **обозревателе решений**.  
  
## <a name="create-a-data-source-from-your-database"></a>Создать источник данных из базы данных  
 Этот шаг использует **мастер настройки источника данных** для создания источника данных, на основе `Region` таблицы в базе данных Northwind. Для создания подключения необходимо иметь доступ к учебной базе данных "Борей". Сведения об установке образца базы данных Northwind см. в разделе [как: установить образцы баз данных](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1.  На **данные** последовательно выберите пункты **Показать источники данных**.  
  
2.  В **источники данных** выберите **добавить новый источник данных** запуск **мастер настройки источника данных**.  
  
3.  На **Выбор типа источника данных** выберите **базы данных**, а затем выберите **Далее**.  
  
4.  На **Выбор подключения базы данных** экрана, выполните одно из следующих действий:  
  
    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
         - или -  
  
    -   Выберите **новое подключение** для запуска **Добавить/изменить подключение** диалоговое окно.  
  
5.  Если базе данных требуется пароль, выберите параметр для включения конфиденциальных данных, а затем выберите **Далее**.  
  
6.  На **Сохранение строки подключения в файле конфигурации приложения** выберите **Далее**.  
  
7.  На **Выбор объектов базы данных** экрана, разверните **таблиц** узла.  
  
8.  Выберите `Region` таблицы, а затем выберите **Готово**.  
  
     **NorthwindDataSet** добавляется в проект и `Region` таблица появляется в **источники данных** окна.  
  
## <a name="add-controls-to-the-form-to-display-the-data"></a>Добавление элементов управления в форму для отображения данных  
 Создавать элементы управления с привязкой к данным путем перетаскивания элементов из **источники данных** на форму.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Создание данных с привязкой к элементам управления в форме Windows  
  
-   Перетащите главный **область** узел из **источники данных** на форму.  
  
     На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Порядок добавления кнопок, вызывающих отдельные методы DbDirect адаптера таблицы  
  
1.  Перетащите три <xref:System.Windows.Forms.Button> управляет из **элементов** на **Form1** (ниже **RegionDataGridView**).  
  
2.  Задайте следующие **имя** и **текст** свойства на каждой кнопке.  
  
    |name|Text|  
    |----------|----------|  
    |`InsertButton`|**Вставить**|  
    |`UpdateButton`|**Обновление**|  
    |`DeleteButton`|**Удалить**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Добавление кода для вставки новых записей в базу данных  
  
1.  Выберите **InsertButton** создайте обработчик событий для события щелчка кнопкой мыши и открыть форму в редакторе кода.  
  
2.  Замените обработчик событий `InsertButton_Click` следующим кодом:  
  
     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Добавление кода для обновления записей в базе данных  
  
1.  Дважды щелкните **UpdateButton** создайте обработчик событий для события щелчка кнопкой мыши и открыть форму в редакторе кода.  
  
2.  Замените обработчик событий `UpdateButton_Click` следующим кодом:  
  
     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Чтобы добавить код для удаления записей из базы данных  
  
1.  Выберите **DeleteButton** создайте обработчик событий для события щелчка кнопкой мыши и открыть форму в редакторе кода.  
  
2.  Замените обработчик событий `DeleteButton_Click` следующим кодом:  
  
     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]  
  
## <a name="run-the-application"></a>Запуск приложения  
  
#### <a name="to-run-the-application"></a>Запуск приложения  
  
-   Выберите **F5** для запуска приложения.  
  
-   Выберите **вставить** кнопку и убедитесь, что новая запись отображается в сетке.  
  
-   Выберите **обновление** кнопку и убедитесь, что запись обновляется в сетке.  
  
-   Выберите **удалить** кнопку и убедитесь, что запись удаляется из сетки.  
  
## <a name="next-steps"></a>Следующие шаги  
 В зависимости от требований приложения существуют несколько шагов, которые возможно потребуется выполнить после создания формы с привязкой к данным. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.  
  
-   Добавление функциональности поиска в форму.  
  
-   Добавление дополнительных таблиц в набор данных, выбрав **настроить набор данных с помощью мастера** изнутри **источники данных** окна. Вы можете добавить элементы управления, отображающие связанные данные, перетащив связанные узлы на форму. Дополнительные сведения см. в разделе [отношения в наборах данных](relationships-in-datasets.md).  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)