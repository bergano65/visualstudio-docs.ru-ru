---
title: Использование таблиц подстановки в привязке данных - элементов управления Windows Forms | Документация Майкрософт
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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e79d4ba6db70876539aa2e85f0579953937cab14
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756328"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Создать пользовательский элемент управления Windows Forms подстановочной привязкой данных
При отображении данных в формах Windows Forms, можно выбрать существующие элементы управления из **элементов**, или можно создать пользовательские элементы управления, если приложению требуются функциональные возможности, недоступные в стандартных элементах управления. В этом пошаговом руководстве демонстрируется создание элемента управления, реализующего <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Элементы управления, реализующие <xref:System.ComponentModel.LookupBindingPropertiesAttribute>, могут содержать три свойства, которые можно привязать к данным. Такие элементы управления похожи на <xref:System.Windows.Forms.ComboBox>.

 Дополнительные сведения о создании элементов управления, см. в разделе [управляет разработки Windows Forms во время разработки](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

 При создании элементов управления для использования в сценариях привязки к данным необходимо реализовать один из следующих атрибутов привязки к данным.

|Использование атрибута привязки данных|
|-----------------------------------|
|Реализуйте <xref:System.ComponentModel.DefaultBindingPropertyAttribute> на простых элементах управления, таких как <xref:System.Windows.Forms.TextBox>, которые отображают отдельный столбец (или свойство) данных. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, который поддерживает простую привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Реализуйте <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.DataGridView>, которые отображают списки (или таблицы) данных. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, который поддерживает сложную привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Реализуйте <xref:System.ComponentModel.LookupBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.ComboBox>, которые отображают списки (или таблицы) данных, но также должны представлять отдельный столбец или отдельное свойство. (Этот процесс описан в данном пошаговом руководстве.)|

 В этом пошаговом руководстве создается элемент управления поиска, который привязан к данным из двух таблиц. В данном примере используются таблицы `Customers` и `Orders` из учебной базы данных "Борей". Элемент управления поиском привязан к `CustomerID` из `Orders` таблицы. Это значение используется для поиска `CompanyName` из `Customers` таблицы.

 В этом пошаговом руководстве описаны следующие процедуры.

-   Создайте новый **приложение Windows Forms**.

-   Добавьте новый **пользовательский элемент управления** в проект.

-   Визуальное проектирование пользовательского элемента управления.

-   Реализация атрибута `LookupBindingProperty`.

-   Создание набора данных с помощью **конфигурации источника данных** мастера.

-   Задайте **CustomerID** столбца на **заказы** таблицы, в **источников данных** окна для использования нового элемента управления.

-   Создание формы для отображения данных в новом элементе управления.

## <a name="prerequisites"></a>Предварительные требования

В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.

1.  Если у вас нет SQL Server Express LocalDB, установите его из [странице загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. В **установщик Visual Studio**, можно установить SQL Server Express LocalDB как часть **хранение и обработка данных** рабочей нагрузки, или в качестве отдельного компонента.

2.  Установка образца базы данных "Борей", выполнив следующие действия:

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранение и обработка данных** рабочей нагрузки в установщике Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на локальном экземпляре LocalDB и выберите **новый запрос**.

       Откроется окно редактора запросов.

    2. Копировать [скрипт Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот сценарий T-SQL создает базу данных "Борей" с нуля и заполняет ее данными.

    3. Вставьте сценарий T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.

       Через некоторое время выполнения запроса отобразятся и создания базы данных Northwind.

## <a name="create-a-windows-forms-application"></a>Создание приложения Windows Forms
 Первым шагом является создание **приложение Windows Forms**.

#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows

1. В Visual Studio на **файл** меню, выберите **New** > **проекта**.

2. Разверните **Visual C#** или **Visual Basic** левой панели, а затем выберите **Windows Desktop**.

3. В средней области выберите **приложения Windows Forms** тип проекта.

4. Назовите проект **LookupControlWalkthrough**, а затем выберите **ОК**.

     **LookupControlWalkthrough** проект создан и добавлен **обозревателе решений**.

## <a name="add-a-user-control-to-the-project"></a>Добавьте в проект пользовательский элемент управления
 В этом пошаговом руководстве создается элемент управления поиска из **пользовательский элемент управления**, поэтому необходимо добавить **пользовательский элемент управления** элемент **LookupControlWalkthrough** проекта.

#### <a name="to-add-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект

1.  Из **проекта** меню, выберите **добавить пользовательский элемент управления**.

2.  Тип `LookupBox` в **имя** области, а затем выберите **добавить**.

     **LookupBox** элемент управления добавляется **обозревателе решений**и откроется в конструкторе.

## <a name="design-the-lookupbox-control"></a>Порядок проектирования элемента управления LookupBox

#### <a name="to-design-the-lookupbox-control"></a>Порядок проектирования элемента управления LookupBox

-   Перетащите <xref:System.Windows.Forms.ComboBox> из **элементов** в область конструктора пользовательского элемента управления.

## <a name="add-the-required-data-binding-attribute"></a>Добавьте необходимый атрибут привязки данных
 Для элементов управления поиска, поддерживающих привязку к данным, можно реализовать <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Реализация атрибута LookupBindingProperties

1.  Коммутатор **LookupBox** элемента управления в представление кода. (На **представление** меню, выберите **кода**.)

2.  Замените код в `LookupBox` следующим кодом:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  В меню **Построение** выберите пункт **Построить решение**.

## <a name="create-a-data-source-from-your-database"></a>Создать источник данных из базы данных
На этом шаге создается источник данных с помощью **конфигурации источника данных** мастера, на основе `Customers` и `Orders` таблиц в базе данных Northwind.

#### <a name="to-create-the-data-source"></a>Создание источника данных

1.  В меню **Данные** выберите команду **Показать источники данных**.

2.  В **источников данных** выберите **добавить новый источник данных** запустить **конфигурации источника данных** мастера.

3.  На странице **Выбор типа источника данных** выберите элемент **База данных** и нажмите **Далее**.

4.  На **Выбор подключения базы данных** странице выполните одно из следующих:

    -   Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

    -   Выберите **новое подключение** для запуска **Добавить/изменить подключение** диалоговое окно.

5.  Если для базы данных требуется пароль, выберите параметр для включения конфиденциальных данных и нажмите кнопку **Далее**.

6.  На **сохранение подключения в файле конфигурации приложения** щелкните **Далее**.

7.  На **Выбор объектов базы данных** странице, разверните узел **таблиц** узла.

8.  Выберите `Customers` и `Orders` таблиц, а затем щелкните **Готово**.

     **NorthwindDataSet** добавляется в проект и `Customers` и `Orders` таблицы отображаются в **источников данных** окна.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Установите для столбца CustomerID таблицы заказов на использование элемента управления LookupBox
 В рамках **источников данных** окно, можно задать элемент управления должен быть создан перед перетаскиванием элементов на форму.

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Порядок настройки столбца CustomerID на привязку к элементу управления LookupBox

1.  Откройте **Form1** в конструкторе.

2.  Разверните **клиентов** узел в **источников данных** окна.

3.  Разверните **заказы** узла (в **клиентов** узла ниже **факсов** столбца).

4.  Щелкните стрелку раскрывающегося списка в **заказы** узел и выберите **сведения** в списке элементов управления.

5.  Щелкните стрелку раскрывающегося списка в **CustomerID** столбца (в **заказы** узла) и выберите **Настройка**.

6.  Выберите **LookupBox** из списка **связанные элементы управления** в **параметры настройки пользовательского интерфейса данных** диалоговое окно.

7.  Нажмите кнопку **ОК**.

8.  Щелкните стрелку раскрывающегося списка в **CustomerID** столбец и выберите **LookupBox**.

## <a name="add-controls-to-the-form"></a>Добавление элементов управления в форму
 Созданием элементов управления с привязкой к данным путем перетаскивания элементов из **источников данных** окна на **Form1**.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Создание элементов управления с привязкой к данным на форме Windows Forms

-   Перетащите **заказы** узел из **источников данных** окна в форму Windows и убедитесь, что **LookupBox** элемент управления используется для отображения данных в `CustomerID` столбец.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Привязка элемента управления для поиска CompanyName из таблицы Customers

#### <a name="to-setup-the-lookup-bindings"></a>Настройка привязок поиска

-   Выберите главный **клиентов** узел в **источников данных** окно и перетащите его в поле со списком в поле **CustomerIDLookupBox** на **Form1** .

     Это задает привязку данных для отображения `CompanyName` из `Customers` таблицы, сохраняя `CustomerID` значение из `Orders` таблицы.

## <a name="running-the-application"></a>Запуск приложения

#### <a name="to-run-the-application"></a>Запуск приложения

-   Нажмите клавишу **F5** для запуска приложения.

-   Перейдите по нескольким записям и убедитесь, что `CompanyName` отображается в `LookupBox` элемента управления.

## <a name="see-also"></a>См. также

- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)