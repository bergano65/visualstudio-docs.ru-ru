---
title: С помощью таблиц подстановки в привязке данных - элементов управления Windows Forms | Документы Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4b3b7c31611c3135477502d3b2a1e2b9d0e19e7e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Создать пользовательский элемент управления Windows Forms, поддерживающих привязку данных подстановки
При отображении данных в формах Windows Forms можно выбрать существующие элементы управления из **элементов**, или можно создать пользовательские элементы управления, если приложение требует функциональные возможности, недоступные в стандартных элементах управления. В этом пошаговом руководстве демонстрируется создание элемента управления, реализующего <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Элементы управления, реализующие <xref:System.ComponentModel.LookupBindingPropertiesAttribute>, могут содержать три свойства, которые можно привязать к данным. Такие элементы управления похожи на <xref:System.Windows.Forms.ComboBox>.

 Дополнительные сведения о разработке элементов управления см. в разделе [разработке элементов управления Windows Forms во время разработки](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

 При создании элементов управления для использования в сценариях привязки к данным необходимо реализовать один из следующих атрибутов привязки к данным:

|Использование атрибута привязки к данным|
|-----------------------------------|
|Реализуйте <xref:System.ComponentModel.DefaultBindingPropertyAttribute> на простых элементах управления, таких как <xref:System.Windows.Forms.TextBox>, которые отображают отдельный столбец (или свойство) данных. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, который поддерживает простую привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Реализуйте <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.DataGridView>, которые отображают списки (или таблицы) данных. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, который поддерживает сложную привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Реализуйте <xref:System.ComponentModel.LookupBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.ComboBox>, которые отображают списки (или таблицы) данных, но также должны представлять отдельный столбец или отдельное свойство. (Этот процесс описан в данном пошаговом руководстве.)|

 В этом пошаговом руководстве создается элемент управления поиска, который привязан к данным из двух таблиц. В данном примере используются таблицы `Customers` и `Orders` из учебной базы данных "Борей". Элемент управления поиска будет привязан к полю `CustomerID` из таблицы `Orders`. Он будет использовать это значение для поиска `CompanyName` в таблице `Customers`.

 В этом пошаговом руководстве описаны следующие процедуры.

-   Создайте новый **приложение Windows Forms**.

-   Добавьте новый **пользовательский элемент управления** в проект.

-   Визуальное проектирование пользовательского элемента управления.

-   Реализация атрибута `LookupBindingProperty`.

-   Создать набор данных с **конфигурации источника данных** мастера.

-   Задать **CustomerID** столбца на **заказов** таблице в **источники данных** окна для использования нового элемента управления.

-   Создание формы для отображения данных в новом элементе управления.

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

4. Назовите проект **LookupControlWalkthrough**, а затем выберите **ОК**.

     **LookupControlWalkthrough** создается проект и добавить **обозревателе решений**.

## <a name="add-a-user-control-to-the-project"></a>Добавьте в проект пользовательский элемент управления
 В этом пошаговом руководстве создается элемент управления поиска из **пользовательский элемент управления**, поэтому добавьте **пользовательский элемент управления** элемент **LookupControlWalkthrough** проекта.

#### <a name="to-add-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект

1.  Из **проекта** последовательно выберите пункты **добавить пользовательский элемент управления**.

2.  Тип `LookupBox` в **имя** области, а затем выберите **добавить**.

     **LookupBox** добавления элемента управления **обозревателе решений**и откроется в конструкторе.

## <a name="design-the-lookupbox-control"></a>Разработки элемента управления LookupBox

#### <a name="to-design-the-lookupbox-control"></a>Порядок проектирования элемента управления LookupBox

-   Перетащите <xref:System.Windows.Forms.ComboBox> из **элементов** рабочую область конструирования пользовательского элемента управления.

## <a name="add-the-required-data-binding-attribute"></a>Добавление необходимого атрибута привязки данных
 Для элементов управления поиска, поддерживающих привязку к данным, можно реализовать <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Реализация атрибута LookupBindingProperties

1.  Коммутатор **LookupBox** элемента управления в представление кода. (На **представление** меню, выберите **кода**.)

2.  Замените код в `LookupBox` следующим кодом:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  В меню **Построение** выберите пункт **Построить решение**.

## <a name="create-a-data-source-from-your-database"></a>Создать источник данных из базы данных
На этом шаге создается источник данных с помощью **конфигурации источника данных**мастера, на основе `Customers` и `Orders` таблицы в базе данных Northwind.

#### <a name="to-create-the-data-source"></a>Создание источника данных

1.  В меню **Данные** выберите команду **Показать источники данных**.

2.  В **источники данных** выберите **добавить новый источник данных** запуск **конфигурации источника данных** мастера.

3.  На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.

4.  На **Выбор подключения базы данных** выполните одно из следующих действий:

    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

    -   Выберите **новое подключение** для запуска **Добавить/изменить подключение** диалоговое окно.

5.  Если базе данных требуется пароль, выберите параметр для включения конфиденциальных данных и нажмите кнопку **Далее**.

6.  На **Сохранение строки подключения в файле конфигурации приложения** щелкните **Далее**.

7.  На **Выбор объектов базы данных** разверните **таблиц** узла.

8.  Выберите `Customers` и `Orders` таблицы, а затем щелкните **Готово**.

     **NorthwindDataSet** добавляется в проект и `Customers` и `Orders` таблицы отображаются в **источники данных** окна.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Значение столбца CustomerID таблицы заказов на использование элемента управления LookupBox
 В пределах **источники данных** окна, можно задать для элемента управления перед перетаскиванием элементов на форму.

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Порядок настройки столбца CustomerID на привязку к элементу управления LookupBox

1.  Откройте **Form1** в конструкторе.

2.  Разверните **клиентов** узел в **источники данных** окна.

3.  Разверните **заказов** узла (в **клиентов** под узлом **факс** столбца).

4.  Щелкните стрелку раскрывающегося списка в **заказов** узел и выберите **сведений** в списке элементов управления.

5.  Щелкните стрелку раскрывающегося списка в **CustomerID** столбца (в **заказов** узла) и выберите **Настройка**.

6.  Выберите **LookupBox** из списка **связанные элементы управления** в **Настройка данных интерфейса** диалоговое окно.

7.  Нажмите кнопку **ОК**.

8.  Щелкните стрелку раскрывающегося списка в **CustomerID** столбец и выберите **LookupBox**.

## <a name="add-controls-to-the-form"></a>Добавление элементов управления в форму
 Можно создать элементы управления с привязкой к данным путем перетаскивания элементов из **источники данных** окна на **Form1**.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Создание элементов управления с привязкой к данным на форме Windows Forms

-   Перетащите **заказов** узел из **источники данных** на форму Windows и убедитесь, что **LookupBox** управления используется для отображения данных в `CustomerID` столбец.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Привязка элемента управления для поиска CompanyName в таблице клиентов

#### <a name="to-setup-the-lookup-bindings"></a>Настройка привязок поиска

-   Выберите главный **клиентов** узел в **источники данных** и перетащите его в поле со списком поле в **CustomerIDLookupBox** на **Form1** .

     Это задается привязка к данным для отображения `CompanyName` из `Customers` таблицы, при этом сохраняя `CustomerID` значение из `Orders` таблицы.

## <a name="running-the-application"></a>Запуск приложения

#### <a name="to-run-the-application"></a>Запуск приложения

-   Нажмите клавишу F5 для запуска приложения.

-   Перейдите по нескольким записям и убедитесь, что `CompanyName` отображается в `LookupBox` элемента управления.

## <a name="see-also"></a>См. также

- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)