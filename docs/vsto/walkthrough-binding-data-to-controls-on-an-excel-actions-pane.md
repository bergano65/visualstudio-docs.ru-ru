---
title: Пошаговое руководство. Привязка данных к элементам управления в панели действий Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de51ead9b3395df1c48f1340e27bd8c891a87fa4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56647011"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Пошаговое руководство. Привязка данных к элементам управления в панели действий Excel
  В этом пошаговом руководстве демонстрируется привязка данных к элементам управления в панели действий в Microsoft Office Excel. Элементы управления показывают отношение «Основной/подробности» между таблицами в базе данных SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В данном пошаговом руководстве рассмотрены следующие задачи:

-   Добавление элементов управления на лист.

-   Создание элемента управления панели действий.

-   Добавление элементов управления Windows Forms с привязкой к данным элемента управления панели действий.

-   Отображение панели действий при открытии приложения.

> [!NOTE]
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

-   Доступ к серверу с образцом базы данных "Борей" SQL Server.

-   Разрешения на чтение и запись к базе данных SQL Server.

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание проекта книги Excel.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1.  Создайте проект книги Excel с именем **панель действий Excel**. В мастере выберите **создания документа**. Дополнительные сведения см. в разделе [Как Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio открывает новую книгу Excel в конструкторе и добавляет **панель действий Excel** проект **обозревателе решений**.

## <a name="add-a-new-data-source-to-the-project"></a>Добавить новый источник данных в проект

### <a name="to-add-a-new-data-source-to-the-project"></a>Чтобы добавить новый источник данных в проект

1. Если **источников данных** окно не отображается, откройте его, в строке меню выберите **представление** > **Other Windows**  >   **Источники данных**.

2. Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

3. Выберите **базы данных** и нажмите кнопку **Далее**.

4. Выберите подключение данных к базе данных SQL Server Northwind или добавьте новое подключение с помощью **новое подключение** кнопки.

5. Нажмите кнопку **Далее**.

6. Очистить параметр, чтобы сохранить подключение, если он выбран, а затем нажмите кнопку **Далее**.

7. Разверните **таблиц** узел в **объектов базы данных** окна.

8. Установите флажок рядом с полем **поставщики** таблицы.

9. Разверните **продуктов** таблицы и выберите **ProductName**, **SupplierID**, **QuantityPerUnit**, и **UnitPrice**.

10. Нажмите кнопку **Готово**.

    Мастер добавляет **поставщики** таблицы и **продуктов** таблицы **источников данных** окна. Он также добавляет типизированный набор данных в проект, который является видимым в **обозревателе решений**.

## <a name="add-controls-to-the-worksheet"></a>Добавление элементов управления на лист
 Затем добавьте <xref:Microsoft.Office.Tools.Excel.NamedRange> управления и <xref:Microsoft.Office.Tools.Excel.ListObject> первый лист элемента управления.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Чтобы добавить элемент управления NamedRange и элемент управления ListObject

1.  Убедитесь, что **Мои Pane.xlsx действий Excel** книга открыта в конструкторе Visual Studio с `Sheet1` отображается.

2.  В **источников данных** окне разверните **поставщики** таблицы.

3.  Щелкните стрелку раскрывающегося списка в **название компании** узел, а затем щелкните **NamedRange**.

4.  Перетащите **название компании** из **источников данных** окно ячейку **A2** в `Sheet1`.

     Объект <xref:Microsoft.Office.Tools.Excel.NamedRange> управления с именем `CompanyNameNamedRange` создается и текст \<CompanyName > отображается в ячейке **A2**. В то же время <xref:System.Windows.Forms.BindingSource> с именем `suppliersBindingSource`, адаптер таблицы и <xref:System.Data.DataSet> добавляются в проект. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource>, который, в свою очередь, привязан к <xref:System.Data.DataSet> экземпляра.

5.  В **источников данных** прокрутите страницу вниз к столбцам, которые находятся под **поставщики** таблицы. В нижней части списка находится **продуктов** таблицы; именно здесь, так как он является дочерним элементом **поставщики** таблицы. Выберите этот параметр, **продуктов** таблицы, не тот, который находится на том же уровне, что **поставщики** таблицы, а затем щелкните стрелку раскрывающегося списка, который отображается.

6.  Нажмите кнопку **ListObject** в раскрывающемся списке, а затем перетащите **продуктов** таблице к ячейке **A6** в `Sheet1`.

     Объект <xref:Microsoft.Office.Tools.Excel.ListObject> управления с именем `ProductNameListObject` создается в ячейке **A6**. В то же время <xref:System.Windows.Forms.BindingSource> с именем `productsBindingSource` и адаптер таблицы добавляются в проект. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource>, который, в свою очередь, привязан к <xref:System.Data.DataSet> экземпляра.

7.  Для C# только выберите **suppliersBindingSource** на область компонентов, а также укажите **модификаторы** свойства **внутренний** в **свойства**  окно.

## <a name="add-controls-to-the-actions-pane"></a>Добавление элементов управления в панели действий
 Далее необходимо, чтобы элемент управления панели действий, имеет поле со списком.

### <a name="to-add-an-actions-pane-control"></a>Чтобы добавить элемент управления панели действий

1.  Выберите **панель действий Excel** в проекте **обозревателе решений**.

2.  В меню **Проект** выберите пункт **Добавить новый элемент**.

3.  В **Добавление нового элемента** выберите **элемента управления панели действий**, назовите его **ActionsControl**и нажмите кнопку **добавить**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Для добавления элементов управления Windows Forms с привязкой к данным элемента управления панели действий

1.  Из **стандартные элементы управления** вкладках **элементов**, перетащите <xref:System.Windows.Forms.ComboBox> управления для элемента управления панели действий.

2.  Изменение **размер** свойства **171, 21**.

3.  Измените размер пользовательского элемента управления в соответствии со списком.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Привязка к данным элемента управления на панели действий
 В этом разделе, необходимо настроить источник данных <xref:System.Windows.Forms.ComboBox> на один и тот же источник данных, как <xref:Microsoft.Office.Tools.Excel.NamedRange> управления на листе.

### <a name="to-set-data-binding-properties-of-the-control"></a>Чтобы задать свойства привязки данных элемента управления

1.  Щелкните правой кнопкой мыши элемента управления панели действий и нажмите кнопку **Просмотр кода**.

2.  Добавьте следующий код, чтобы <xref:System.Windows.Forms.UserControl.Load> событий элемента управления панели действий.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3.  В C#, необходимо создать обработчик событий для `ActionsControl`. Можно поместить этот код в `ActionsControl` конструктор. Дополнительные сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Показать панель действий
 Панель действий не отображается, пока не будет добавлен элемент управления во время выполнения.

#### <a name="to-show-the-actions-pane"></a>Чтобы отобразить панель действий

1.  В **обозревателе решений**, щелкните правой кнопкой мыши *ThisWorkbook.vb* или *ThisWorkbook.cs*, а затем нажмите кнопку **Просмотр кода**.

2.  Создайте новый экземпляр пользовательского элемента управления в `ThisWorkbook` класса.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3.  В <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> обработчик событий `ThisWorkbook`, добавьте элемент управления панели действий.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно проверить документ, чтобы убедиться, что панель действий открывается при открытии документа, и что элементы управления имеют отношение "основной/подробности".

### <a name="to-test-your-document"></a>Проверка документа

1.  Нажмите клавишу **F5** для запуска проекта.

2.  Убедитесь, что панель действий является видимым.

3.  Выберите название компании в поле со списком. Убедитесь, что указано имя компании в <xref:Microsoft.Office.Tools.Excel.NamedRange> управления и что сведения о продукте, перечислены в <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления.

4.  Выберите разные компании, чтобы проверить имя компании и сведения о продукте измените соответствующим образом.

## <a name="next-steps"></a>Следующие шаги
 Ниже приводятся некоторые из возможных последующих задач.

-   Привязка данных к элементам управления в Word. Дополнительные сведения см. в разделе [Пошаговое руководство: Привязка данных к элементам управления в панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

-   Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>См. также
- [Общие сведения о панели действий](../vsto/actions-pane-overview.md)
- [Практическое руководство. Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
