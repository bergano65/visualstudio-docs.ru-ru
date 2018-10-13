---
title: Передача данных между формами | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9f28902673018a4ae90fbb2ed83e741be99fbfc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204832"
---
# <a name="pass-data-between-forms"></a>Передача данных между формами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Это пошаговое руководство содержит инструкции по передаче данных из одной формы в другую. Использование таблиц customers и orders из Northwind, одна форма позволяет пользователям выбрать клиента и второй форме отображаются заказы выбранного клиента. В этом пошаговом руководстве показано, как создать метод на второй форме, которая получает данные из первой формы.  
  
> [!NOTE]
>  Здесь демонстрируется всего один способ передачи данных между формами. Существуют другие способы передать данные в форму, включая создание второй конструктор для получения данных, или создание общедоступного свойства, которое можно задать с помощью данных из первой формы.  
  
 В данном пошаговом руководстве представлены следующие задачи.  
  
-   Создание нового **приложения Windows** проекта.  
  
-   Создание и настройка набора данных с помощью [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Выбор элемента управления, создаваемого на форме при перетаскивании элементов из **источников данных** окна. Дополнительные сведения см. в разделе [задать для элемента управления создается при перетаскивании из окна источников данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Создание элемента управления с привязкой к данным путем перетаскивания элементов из **источников данных** окна в форму.  
  
-   Создание второй формы с сеткой для отображения данных.  
  
-   Создание запроса адаптера таблицы для получения заказов определенного клиента.  
  
-   Передача данных между формами.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства требуется:  
  
-   Доступ к примеру базы данных "Борей". Дополнительные сведения см. в разделе [как: установить образцы баз данных](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-the-windows-application"></a>Создание приложения Windows  
  
#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows  
  
1.  Из **файл** меню, создайте новый проект.  
  
2.  Задайте для проекта имя `PassingDataBetweenForms`.  
  
3.  Выберите **приложение Windows Forms**и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [клиентских приложений](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **PassingDataBetweenForms** проект создан и добавлен **обозревателе решений**.  
  
## <a name="create-the-data-source"></a>Создание источника данных  
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1.  В меню **Данные** выберите команду **Показать источники данных**.  
  
2.  В **источников данных** выберите **добавить новый источник данных** запустить **конфигурации источника данных** мастера.  
  
3.  На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.  
  
4.  На **Выбор модели базы данных** странице, убедитесь, что **набора данных** указан, а затем нажмите кнопку **Далее**.  
  
5.  На **Выбор подключения базы данных** выполните одно из следующих:  
  
    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
    -   Выберите **новое подключение** для запуска **Добавить/изменить подключение** диалоговое окно.  
  
6.  Если базе данных требуется пароль и включен параметр для включения конфиденциальных данных, выберите параметр и нажмите кнопку **Далее**.  
  
7.  На **сохранение подключения в файле конфигурации приложения** щелкните **Далее**.  
  
8.  На **Выбор объектов базы данных** странице, разверните узел **таблиц** узла.  
  
9. Выберите **клиентов** и **заказы** таблиц, а затем щелкните **Готово**.  
  
     **NorthwindDataSet** добавляется в проект и **клиентов** и **заказы** таблицы отображаются в **источников данных** окна.  
  
## <a name="create-the-first-form-form1"></a>Создание первой формы (Form1)  
 Можно создать сетку с привязкой к данным ( <xref:System.Windows.Forms.DataGridView> управления), путем перетаскивания **клиентов** узел из **источников данных** окна в форму.  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Создание сетки с привязкой к данным на форме  
  
-   Перетащите главный **клиентов** узел из **источников данных** окна на **Form1**.  
  
     Объект <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям, отображаются на **Form1**. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.  
  
## <a name="create-the-second-form-form2"></a>Создание второй формы (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Порядок создания второй формы, предназначенной для передачи данных  
  
1.  В меню **Проект** выберите пункт **Добавить форму Windows**.  
  
2.  Оставьте имя по умолчанию **Form2**и нажмите кнопку **добавить**.  
  
3.  Перетащите главный **заказы** узел из **источников данных** окна на **Form2**.  
  
     Объект <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям, отображаются на **Form2**. Объект [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, и <xref:System.Windows.Forms.BindingNavigator> отображаются в области компонентов.  
  
4.  Удалить **OrdersBindingNavigator** из области компонентов.  
  
     **OrdersBindingNavigator** исчезнет из **Form2**.  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Добавление запроса адаптера таблицы на форму Form2 для загрузки заказов выбранного клиента на форме Form1  
  
#### <a name="to-create-a-tableadapter-query"></a>Для создания запроса адаптера таблицы  
  
1.  Дважды щелкните **NorthwindDataSet.xsd** файл **обозревателе решений**.  
  
2.  Щелкните правой кнопкой мыши **OrdersTableAdapter**и выберите **добавить запрос**.  
  
3.  Оставьте значение настройки по умолчанию **использовать инструкции SQL**, а затем нажмите кнопку **Далее**.  
  
4.  Оставьте значение настройки по умолчанию **SELECT, возвращающая строки**, а затем нажмите кнопку **Далее**.  
  
5.  Добавить предложение WHERE для запроса, чтобы получить `Orders` на основе `CustomerID`. Запрос должен выглядеть примерно следующим образом:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Проверьте правильность синтаксиса параметров для своей базы данных. Например, в Microsoft Access предложение WHERE должно выглядеть следующим образом: `WHERE CustomerID = ?`.  
  
6.  Нажмите кнопку **Далее**.  
  
7.  Для **заполнения имя DataTableMethod**, тип `FillByCustomerID`.  
  
8.  Очистить **возвращение DataTable** , а затем щелкните **Далее**.  
  
9. Нажмите кнопку **Готово**.  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>Создание метода на форме Form2 для передачи данных  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>Порядок создания метода, предназначенного для передачи данных  
  
1.  Щелкните правой кнопкой мыши **Form2**и выберите **Просмотр кода** открыть **Form2** в **редактор кода**.  
  
2.  Добавьте следующий код, чтобы **Form2** после `Form2_Load` метод:  
  
     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Создание метода на форме Form1 для передачи данных и отображения Form2  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Порядок создания метода, предназначенного для передачи данных в Form2  
  
1.  В **Form1**, щелкните правой кнопкой мыши сетку данных клиентов и нажмите кнопку **свойства**.  
  
2.  В **свойства** окно, нажмите кнопку **события**.  
  
3.  Дважды щелкните **CellDoubleClick** событий.  
  
     Откроется окно редактора кода.  
  
4.  Обновите определение метода в соответствии со следующим примером:  
  
     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]  
  
## <a name="run-the-application"></a>Запуск приложения  
  
#### <a name="to-run-the-application"></a>Запуск приложения  
  
-   Нажмите клавишу F5 для запуска приложения.  
  
-   Дважды щелкните запись клиента в **Form1** открыть **Form2** с заказов этого клиента.  
  
## <a name="next-steps"></a>Следующие шаги  
 В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после передачи данных между формами. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.  
  
-   Изменение набора данных для добавления или удаления объектов базы данных. Дополнительные сведения см. в разделе, посвященном [созданию и настройке наборов данных](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Добавление функциональности для сохранения данных в базу данных. Дополнительные сведения см. в разделе [сохранить данные в базе данных](../data-tools/save-data-back-to-the-database.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

