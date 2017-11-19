---
title: "Создание пользовательского элемента управления Windows Forms с привязкой данных | Документы Microsoft"
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 8b23bfe7c30988a80904377e583a5a5f6d4cd2ff
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Создать пользовательский элемент управления Windows Forms, который поддерживает сложную привязку данных
При отображении данных на формах в приложениях Windows, можно выбрать существующие элементы управления из **элементов**, или можно создать пользовательские элементы управления, если приложение требует функциональные возможности, недоступные в стандартных элементах управления. В этом пошаговом руководстве демонстрируется создание элемента управления, реализующего <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Элементы управления, реализующие <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, содержат свойство `DataSource` и `DataMember`, которое можно привязать к данным. Такие элементы управления похожи на <xref:System.Windows.Forms.DataGridView> или<xref:System.Windows.Forms.ListBox>  
  
 Дополнительные сведения о разработке элементов управления см. в разделе [разработке элементов управления Windows Forms во время разработки](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).  
  
 При создании элементов управления для использования в сценариях привязки к данным необходимо реализовать один из следующих атрибутов привязки к данным:  
  
|Использование атрибута привязки к данным|  
|-----------------------------------|  
|Реализуйте <xref:System.ComponentModel.DefaultBindingPropertyAttribute> на простых элементах управления, таких как <xref:System.Windows.Forms.TextBox>, которые отображают отдельный столбец (или свойство) данных. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, который поддерживает простую привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Реализуйте <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.DataGridView>, которые отображают списки (или таблицы) данных. (Этот процесс описан в данном пошаговом руководстве.)|  
|Реализуйте <xref:System.ComponentModel.LookupBindingPropertiesAttribute> на элементах управления, таких как <xref:System.Windows.Forms.ComboBox>, которые отображают списки (или таблицы) данных, но также должны представлять отдельный столбец или отдельное свойство. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, поддерживающих привязку данных подстановки](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 В этом пошаговом руководстве создается сложный элемент управления, отображающий строки данных из таблицы. В данном примере используется таблица `Customers` из учебной базы данных "Борей". Сложный элемент управления отображает таблицу клиентов в <xref:System.Windows.Forms.DataGridView> в пользовательском элементе управления.  
  
 В этом пошаговом руководстве описаны следующие процедуры.  
  
-   Создайте новый **приложение Windows Forms**.  
  
-   Добавьте новый **пользовательский элемент управления** в проект.  
  
-   Визуальное проектирование пользовательского элемента управления.  
  
-   Реализация атрибута `ComplexBindingProperty`.  
  
-   Создать набор данных с [мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Задать **клиентов** в таблицу [окно "Источники данных"](add-new-data-sources.md) для использования нового сложного элемента управления.  
  
-   Добавьте новый элемент управления, перетащив его из **окно "Источники данных"** на **Form1**.  
  
## <a name="prerequisites"></a>Предварительные требования  
В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.  
  
1.  Если у вас нет SQL Server Express LocalDB, установите его из [страница загрузки выпуски SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), либо с помощью **установщик Visual Studio**. Установщик Visual Studio можно установить SQL Server Express LocalDB в рамках **хранения и обработки данных** рабочей нагрузки, или в отдельных компонентов.  
  
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

4. Назовите проект **ComplexControlWalkthrough**, а затем выберите **ОК**. 
  
     **ComplexControlWalkthrough** создается проект и добавить **обозревателе решений**.  
  
## <a name="add-a-user-control-to-the-project"></a>Добавьте в проект пользовательский элемент управления  
 Поскольку в этом пошаговом руководстве создается сложный элемент управления можно привязать к данным из **пользовательский элемент управления**, необходимо добавить **пользовательский элемент управления** в проект.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект  
  
1.  Из **проекта** меню, выберите **добавить пользовательский элемент управления**.  
  
2.  Тип **ComplexDataGridView** в **имя** области, а затем выберите **добавить**.  
  
     **ComplexDataGridView** добавления элемента управления **обозревателе решений**и откроется в конструкторе.  
  
## <a name="design-the-complexdatagridview-control"></a>Конструктор элемента управления ComplexDataGridView  
 Этот этап добавляет <xref:System.Windows.Forms.DataGridView> в пользовательский элемент управления.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>Порядок проектирования элемента управления ComplexDataGridView  
  
-   Перетащите <xref:System.Windows.Forms.DataGridView> из **элементов** рабочую область конструирования пользовательского элемента управления.  
  
## <a name="add-the-required-data-binding-attribute"></a>Добавление необходимого атрибута привязки данных  
 Для сложных элементов управления, поддерживающих привязку к данным, можно реализовать <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Реализация атрибута ComplexBindingProperties  
  
1.  Коммутатор **ComplexDataGridView** элемента управления в представление кода. (На **представление** последовательно выберите пункты **кода**.)  
  
2.  Замените код в `ComplexDataGridView` следующим кодом:  
  
     [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]  
  
3.  В меню **Построение** выберите пункт **Построить решение**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Создание источника данных из базы данных  
Этот шаг использует **конфигурации источника данных** мастер для создания источника данных на основе `Customers` таблицы в базе данных Northwind.  
  
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
  
8.  Выберите `Customers` , а затем выберите пункт **Готово**.  
  
     **NorthwindDataSet** добавляется в проект и `Customers` таблица появляется в **источники данных** окна.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Задайте таблицы клиентов на использование элемента управления ComplexDataGridView  
 В пределах **источники данных** окна, можно задать для элемента управления перед перетаскиванием элементов на форму.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Порядок настройки таблицы клиентов на привязку к элементу управления ComplexDataGridView  
  
1.  Откройте **Form1** в конструкторе.  
  
2.  Разверните **клиентов** узел в **источники данных** окна.  
  
3.  Щелкните стрелку раскрывающегося списка в **клиентов** узел и выберите **Настройка**.  
  
4.  Выберите **ComplexDataGridView** из списка **связанные элементы управления** в **Настройка данных интерфейса** диалоговое окно.  
  
5.  Щелкните стрелку раскрывающегося списка в `Customers` таблицы, а затем выберите **ComplexDataGridView** в списке элементов управления.  
  
## <a name="add-controls-to-the-form"></a>Добавление элементов управления в форму  
 Можно создать элементы управления с привязкой к данным путем перетаскивания элементов из **источники данных** на форму.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Создание элементов управления с привязкой к данным на форме  
  
-   Перетащите главный **клиентов** узел из **источники данных** на форму. Убедитесь, что **ComplexDataGridView** управления используется для отображения данных таблицы.  
  
## <a name="running-the-application"></a>Запуск приложения  
  
#### <a name="to-run-the-application"></a>Запуск приложения  
  
-   Нажмите клавишу F5 для запуска приложения.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после создания элемента управления, поддерживающего привязку к данным. Некоторые типичные дальнейшие действия.  
  
-   Помещение пользовательских элементов управления в библиотеку элементов управления, чтобы их можно было повторно использовать в других приложениях.  
  
-   Создание элементов управления, поддерживающих сценарии поиска. Дополнительные сведения см. в разделе [создать пользовательский элемент управления Windows Forms, поддерживающих привязку данных подстановки](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Задать для элемента управления создается при перетаскивании из окна "Источники данных"](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Элементы управления Windows Forms](/dotnet/framework/winforms/controls/index)
