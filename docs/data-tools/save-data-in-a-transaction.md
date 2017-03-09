---
title: "Пошаговое руководство. Сохранение данных в транзакции | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "данные [Visual Studio], сохранение в транзакциях"
  - "сохранение данных"
  - "System.Transactions - пространство имен"
  - "Transactions - пространство имен"
  - "транзакции, сохранение данных"
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Пошаговое руководство. Сохранение данных в транзакции
В этом пошаговом руководстве демонстрируется сохранение данных в транзакции с помощью пространства имен <xref:System.Transactions>.  В данном примере используются таблицы `Customers` и `Orders` из учебной базы данных "Борей".  
  
## Обязательные компоненты  
 В данном пошаговом руководстве требуется доступ к учебной базе данных "Борей".  Дополнительные сведения о настройке учебной базы данных "Борей" см. в разделе [Практическое руководство. Установка образцов баз данных](../data-tools/how-to-install-sample-databases.md).  
  
## Создание приложения Windows  
 Первым шагом является создание **Приложения Windows**.  
  
#### Порядок создания нового проекта Windows  
  
1.  В меню **Файл** Visual Studio создайте новый **Проект**.  
  
2.  Присвойте проекту имя "SavingDataInATransactionWalkthrough".  
  
3.  Выберите **Приложение Windows** и нажмите кнопку **ОК**.  Для получения дополнительной информации см. [Клиентские приложения](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Создается проект **SavingDataInATransactionWalkthrough**, который добавляется в **Обозреватель решений**.  
  
## Создание источника данных в виде базы данных  
 В этом шаге [мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png) используется для создания источника данных на основе таблиц `Customers` и `Orders` в учебной базе данных "Борей".  
  
#### Создание источника данных  
  
1.  В меню **Данные** выберите команду **Показать источники данных**.  
  
2.  В окне **Источники данных** выберите **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.  
  
3.  На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.  
  
4.  На странице **Выбор подключения к базе данных** выполните одно из следующих действий.  
  
    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
         \-или\-  
  
    -   Выберите **Новое подключение** для открытия диалогового окна **Добавить\/изменить подключение** и создайте новое подключение к базе данных "Борей".  
  
5.  Если базе данных требуется пароль, выберите параметр для включения конфиденциальных данных и щелкните **Далее**.  
  
6.  На странице **Сохранение подключения в файле конфигурации приложения** нажмите кнопку **Далее**.  
  
7.  Разверните узел **Таблицы** на странице **Выбор объектов базы данных**.  
  
8.  Выберите таблицы `Customers` и `Orders` и нажмите кнопку **Готово**.  
  
     Объект **NorthwindDataSet** добавляется в проект, и таблицы `Customers` и `Orders` отображаются в окне **Источники данных**.  
  
## Добавление элементов управления на форму  
 Вы можете создавать элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.  
  
#### Создание элементов управления с привязкой к данным на форме Windows Forms  
  
-   Разверните узел **Клиенты** в окне **Источники данных**.  
  
-   Перетащите главный узел **Клиенты** из окна **Источники данных** на **Form1**.  
  
     На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов \(<xref:System.Windows.Forms.BindingNavigator>\) для перемещения по записям.  В области компонентов появляется [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> и <xref:System.Windows.Forms.BindingNavigator>.  
  
-   Перетащите связанный узел **Заказы** \(связанный узел дочерней таблицы под столбцом **Факс**, а не главный узел **Заказы**\) на форму под **CustomersDataGridView**.  
  
     На форме появляется <xref:System.Windows.Forms.DataGridView>.  В области компонентов отображается [OrdersTableAdapter](../data-tools/tableadapter-overview.md) и <xref:System.Windows.Forms.BindingSource>.  
  
## Добавление ссылки на сборку System.Transactions  
 Транзакции используют пространство имен <xref:System.Transactions>.  Ссылка проекта на сборку system.transactions не добавляется по умолчанию, поэтому вам нужно добавить ее вручную.  
  
#### Порядок добавления ссылки на DLL\-файл System.Transactions  
  
1.  В меню **Проект** выберите пункт **Добавить ссылку**.  
  
2.  Выберите **System.Transactions** \(на вкладке **.NET**\) и нажмите кнопку **ОК**.  
  
     Ссылка на **System.Transactions** добавляется в проект.  
  
## Изменение кода в кнопке SaveItem объекта BindingNavigator  
 По умолчанию для первой перетащенной на форму таблицы в событие `click` кнопки сохранения в <xref:System.Windows.Forms.BindingNavigator> добавляется код.  Для обновления дополнительных таблиц вам необходимо добавить такой код вручную.  В этом пошаговом руководстве мы выполнили рефакторинг имеющегося кода сохранения из обработчика события щелчка кнопки сохранения и создали несколько дополнительных методов для предоставления определенной функциональности обновления, основанной на потребности в добавлении или удалении строки.  
  
#### Изменение автоматически сформированного кода сохранения  
  
1.  Дважды нажмите кнопку **Сохранить** на **CustomersBindingNavigator** \(кнопка со значком гибкого диска\).  
  
2.  Замените метод `CustomersBindingNavigatorSaveItem_Click` следующим кодом:  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
 При согласовании изменений связанных данных применяется следующий порядок.  
  
-   Удалите дочерние записи \(в данном случае удалите записи из таблицы `Orders`\).  
  
-   Удалите родительские записи \(в данном случае удалите записи из таблицы `Customers`\).  
  
-   Вставьте родительские записи \(в данном случае вставьте записи в таблицу `Customers`\).  
  
-   Вставьте дочерние записи \(в данном случае вставьте записи в таблицу `Orders`\).  
  
#### Удаление существующих заказов  
  
-   Добавьте следующий метод `DeleteOrders` в **Form1**:  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-cs[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### Удаление существующих клиентов  
  
-   Добавьте следующий метод `DeleteCustomers` в **Form1**:  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-cs[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### Добавление новых клиентов  
  
-   Добавьте следующий метод `AddNewCustomers` в **Form1**:  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-cs[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### Добавление новых заказов  
  
-   Добавьте следующий метод `AddNewOrders` в **Form1**:  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-cs[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## Запуск приложения  
  
#### Запуск приложения  
  
-   Нажмите клавишу F5 для запуска приложения.  
  
## См. также  
 [Транзакции и параллелизм](../Topic/Transactions%20and%20Concurrency.md)   
 [Распределенные транзакции Oracle](../Topic/Oracle%20Distributed%20Transactions.md)   
 [Практическое руководство. Сохранение данных с помощью транзакции](../data-tools/save-data-by-using-a-transaction.md)   
 [Интеграция System.Transactions с SQL Server](../Topic/System.Transactions%20Integration%20with%20SQL%20Server.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Сохранение данных](../data-tools/saving-data.md)