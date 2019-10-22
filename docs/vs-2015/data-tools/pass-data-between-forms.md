---
title: Передача данных между формами | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e14165ba2111f40898c00b3d01950425c042070
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652913"
---
# <a name="pass-data-between-forms"></a>Передача данных между формами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это пошаговое руководство содержит инструкции по передаче данных из одной формы в другую. Используя таблицы Customers и Orders из Northwind, одна форма позволяет пользователям выбрать клиента, а вторая — заказы выбранного клиента. В этом пошаговом руководстве показано, как создать метод во второй форме, которая получает данные из первой формы.

> [!NOTE]
> Здесь демонстрируется всего один способ передачи данных между формами. Существуют и другие варианты передачи данных в форму, в том числе создание второго конструктора для получения данных или создание открытого свойства, которое можно задать с помощью данных из первой формы.

 В данном пошаговом руководстве представлены следующие задачи.

- Создание нового проекта **приложения Windows** .

- Создание и настройка набора данных с помощью [мастера настройки источника данных](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Выбор элемента управления, создаваемого на форме при перетаскивании элементов из окна **Источники данных**. Дополнительные сведения см. в разделе [Установка элемента управления, создаваемого при перетаскивании из окна Источники данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Создание элемента управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.

- Создание второй формы с сеткой для отображения данных.

- Создание запроса адаптера таблицы для получения заказов определенного клиента.

- Передача данных между формами.

## <a name="prerequisites"></a>Необходимые компоненты
 Для выполнения данного пошагового руководства требуется:

- Доступ к примеру базы данных "Борей".

## <a name="create-the-windows-application"></a>Создание приложения Windows

#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows

1. В меню **файл** создайте новый проект.

2. Задайте для проекта имя `PassingDataBetweenForms`.

3. Выберите **Windows Forms приложение**и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [Client Applications](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Создается проект **PassingDataBetweenForms**, который добавляется в **Обозреватель решений**.

## <a name="create-the-data-source"></a>Создание источника данных

#### <a name="to-create-the-data-source"></a>Создание источника данных

1. В меню **Данные** выберите команду **Показать источники данных**.

2. В окне **Источники данных** выберите **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.

3. На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.

4. На странице **Выбор модели базы данных** выберите **Набор данных** и нажмите кнопку **Далее**.

5. На странице **Выбор подключения к базе данных** выполните одно из следующих действий:

    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

    - Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение**.

6. Если базе данных требуется пароль и выбран параметр для включения конфиденциальных данных, выберите параметр и нажмите кнопку **Далее**.

7. На странице **Сохранение подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

8. Разверните узел **Таблицы** на странице **Выбор объектов базы данных**.

9. Выберите таблицы **Customers** и **Orders** и нажмите кнопку **Готово**.

     **NorthwindDataSet** добавляется в проект, и таблицы **Customers** и **Orders** отображаются в окне **Источники данных**.

## <a name="create-the-first-form-form1"></a>Создание первой формы (Form1)
 Вы можете создать сетку с привязкой к данным (элемент управления <xref:System.Windows.Forms.DataGridView>) с помощью перетаскивания узла **Customers** из окна **Источники данных** на форму.

#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Создание сетки с привязкой к данным на форме

- Перетащите главный узел **Customers** из окна **Источники данных** на форму **Form1**.

     На форме **Form1** появляется <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. В области компонентов появляется [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> и <xref:System.Windows.Forms.BindingNavigator>.

## <a name="create-the-second-form-form2"></a>Создание второй формы (Form2)

#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Порядок создания второй формы, предназначенной для передачи данных

1. В меню **Проект** выберите пункт **Добавить форму Windows**.

2. Оставьте имя по умолчанию **Form2** и нажмите кнопку **Добавить**.

3. Перетащите главный узел **Orders** из окна **Источники данных** на форму **Form2**.

     На форме **Form2** появляется <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. В области компонентов появляется [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> и <xref:System.Windows.Forms.BindingNavigator>.

4. Удалите **OrdersBindingNavigator** из области компонентов.

     **OrdersBindingNavigator** исчезает из **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Добавление запроса TableAdapter в форму Form2 для загрузки заказов выбранного клиента на Form1

#### <a name="to-create-a-tableadapter-query"></a>Создание запроса TableAdapter

1. Дважды щелкните файл **NorthwindDataSet.xsd** в **обозревателе решений**.

2. Щелкните правой кнопкой мыши элемент **OrdersTableAdapter** и выберите пункт **Добавить запрос**.

3. Оставьте параметр по умолчанию **Использовать инструкции SQL** и нажмите кнопку **Далее**.

4. Оставьте параметр по умолчанию **Инструкция SELECT, возвращающая строки** и нажмите кнопку **Далее**.

5. Добавьте в запрос предложение WHERE, чтобы возвратить `Orders` на основании `CustomerID`. Запрос должен выглядеть примерно следующим образом:

    ```
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Проверьте правильность синтаксиса параметров для своей базы данных. Например, в Microsoft Access предложение WHERE должно выглядеть следующим образом: `WHERE CustomerID = ?`.

6. Нажмите кнопку **Далее**.

7. В качестве **имени дататаблемесод**введите `FillByCustomerID`.

8. Снимите флажок **Вернуть таблицу данных (DataTable)** и нажмите кнопку **Далее**.

9. Нажмите кнопку **Готово**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Создание метода на Form2 для передачи данных

#### <a name="to-create-a-method-to-pass-data-to"></a>Порядок создания метода, предназначенного для передачи данных

1. Щелкните правой кнопкой мыши **Form2** и выберите пункт **Просмотреть код**, чтобы открыть **Form2** в **редакторе кода**.

2. Добавьте следующий код в **Form2** после метода `Form2_Load`:

     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Создание метода на Form1 для передачи данных и показа Form2

#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Порядок создания метода, предназначенного для передачи данных в Form2

1. В **Form1** щелкните правой кнопкой мыши сетку данных клиентов и выберите пункт **Свойства**.

2. В окне **Свойства** выберите **События**.

3. Дважды щелкните событие **CellDoubleClick**.

     Откроется окно редактора кода.

4. Обновите определение метода в соответствии со следующим примером:

     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]

## <a name="run-the-application"></a>Запуск приложения

#### <a name="to-run-the-application"></a>Запуск приложения

- Нажмите клавишу F5 для запуска приложения.

- Дважды щелкните запись клиента в форме **Form1**, чтобы открыть **Form2** с заказами этого клиента.

## <a name="next-steps"></a>Следующие шаги
 В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после передачи данных между формами. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.

- Изменение набора данных для добавления или удаления объектов базы данных. Дополнительные сведения см. в разделе, посвященном [созданию и настройке наборов данных](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Добавление функциональности для сохранения данных в базу данных. Дополнительные сведения см. [в разделе Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>См. также раздел
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
