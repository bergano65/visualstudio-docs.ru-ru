---
title: "Пошаговое руководство: Привязка данных к элементам управления в панели действий Excel | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: "63"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 11a9f55691416a1b7775e0ff9d392293d9fee33f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-data-to-controls-on-an-excel-actions-pane"></a>Пошаговое руководство. Привязка данных к элементам управления в панели действий Excel
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
  
-   Разрешения на чтение и запись в базу данных SQL Server.  
  
## <a name="creating-the-project"></a>Создание проекта  
 Первым шагом является создание проекта книги Excel.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект книги Excel с именем **Моя панель действий Excel**. В мастере выберите **создания документа**. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio открывает новую книгу Excel в конструкторе и добавляет **Моя панель действий Excel** проекта **обозревателе решений**.  
  
## <a name="adding-a-new-data-source-to-the-project"></a>Добавление нового источника данных в проект  
  
#### <a name="to-add-a-new-data-source-to-the-project"></a>Чтобы добавить новый источник данных в проект  
  
1.  Если окно **Источники данных** не отображается, откройте его, выбрав в строке меню пункты **Вид**, **Другие окна**, **Источники данных**.  
  
2.  Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.  
  
3.  Выберите **базы данных** и нажмите кнопку **Далее**.  
  
4.  Выберите подключение данных к базе данных Northwind SQL Server или добавьте новое подключение с помощью **новое подключение** кнопки.  
  
5.  Нажмите кнопку **Далее**.  
  
6.  Удалить параметр, чтобы сохранить подключение, если он установлен, а затем щелкните **Далее**.  
  
7.  Разверните **таблиц** узел в **объектов базы данных** окна.  
  
8.  Установите флажок рядом с **поставщики** таблицы.  
  
9. Разверните **продуктов** таблицы и выберите **ProductName**, **SupplierID**, **QuantityPerUnit**, и **UnitPrice**.  
  
10. Нажмите кнопку **Готово**.  
  
 Мастер добавит **поставщики** таблицы и **продуктов** таблицы, к **источники данных** окна. Он также добавляет типизированный набор данных в проект, который является видимым в **обозревателе решений**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Добавление элементов управления на лист  
 Добавьте <xref:Microsoft.Office.Tools.Excel.NamedRange> управления и <xref:Microsoft.Office.Tools.Excel.ListObject> первый лист элемента управления.  
  
#### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Добавление элемента управления NamedRange и элемент управления ListObject  
  
1.  Убедитесь, что **Мои Pane.xlsx действия Excel** книга открыта в конструкторе Visual Studio с `Sheet1` отображается.  
  
2.  В **источники данных** окна, разверните **поставщики** таблицы.  
  
3.  Щелкните стрелку раскрывающегося списка в **название компании** , а затем щелкните **NamedRange**.  
  
4.  Перетащите **название компании** из **источники данных** окна ячейку **A2** в `Sheet1`.  
  
     Объект <xref:Microsoft.Office.Tools.Excel.NamedRange> управления с именем `CompanyNameNamedRange` создается и текст \<CompanyName > отображается в ячейке **A2**. В то же время <xref:System.Windows.Forms.BindingSource> с именем `suppliersBindingSource`, адаптер таблиц и <xref:System.Data.DataSet> добавляются в проект. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource>, который, в свою очередь, привязан к <xref:System.Data.DataSet> экземпляра.  
  
5.  В **источники данных** прокрутите вниз к столбцам, которые находятся в **поставщики** таблицы. В нижней части списка — **продуктов** таблицы; именно здесь, так как он является дочерним элементом **поставщики** таблицы. Выберите этот параметр, **продуктов** таблицы не того, который находится на том же уровне, как **поставщики** таблицы, а затем щелкните стрелку раскрывающегося списка, которая появляется.  
  
6.  Нажмите кнопку **ListObject** в раскрывающемся списке, а затем перетащите **продуктов** таблицы ячейку **A6** в `Sheet1`.  
  
     Объект <xref:Microsoft.Office.Tools.Excel.ListObject> управления с именем `ProductNameListObject` создается в ячейке **A6**. В то же время <xref:System.Windows.Forms.BindingSource> с именем `productsBindingSource` и адаптер таблицы добавляются в проект. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource>, который, в свою очередь, привязан к <xref:System.Data.DataSet> экземпляра.  
  
7.  Только в C#, выберите **suppliersBindingSource** на область компонентов, а также укажите **модификаторы** свойства **внутренний** в **свойства** окна.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Добавление элементов управления в панели действий  
 Далее необходимо, чтобы элемент управления панели действий, который содержит поле со списком.  
  
#### <a name="to-add-an-actions-pane-control"></a>Чтобы добавить элемент управления панели действий  
  
1.  Выберите **Моя панель действий Excel** проекта в **обозревателе решений**.  
  
2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
3.  В **Добавление нового элемента** выберите **управления панели действий**, назовите его **ActionsControl**и нажмите кнопку **добавить**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Для добавления элементов управления Windows Forms с привязкой к данным элемента управления панели действий  
  
1.  Из **стандартные элементы управления** вкладках **элементов**, перетащите <xref:System.Windows.Forms.ComboBox> элемента управления к элементу управления панели действий.  
  
2.  Изменение **размер** свойства **171, 21**.  
  
3.  Изменение размера пользовательского элемента управления в соответствии со списком.  
  
## <a name="binding-the-control-on-the-actions-pane-to-data"></a>Привязка к данным элемента управления в панели действий  
 В этом разделе будет Настройка источника данных объекта <xref:System.Windows.Forms.ComboBox> с одним источником данных, как <xref:Microsoft.Office.Tools.Excel.NamedRange> управления на листе.  
  
#### <a name="to-set-data-binding-properties-of-the-control"></a>Чтобы задать свойства привязки данных элемента управления  
  
1.  Щелкните правой кнопкой мыши элемент управления панели действий и нажмите кнопку **Просмотр кода**.  
  
2.  Добавьте следующий код в <xref:System.Windows.Forms.UserControl.Load> события элемента управления панели действий.  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  В C# необходимо создать обработчик событий для `ActionsControl`. Можно заменить этот код в `ActionsControl` конструктора. Дополнительные сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="showing-the-actions-pane"></a>Отображение панели действий  
 Панель действий не отображается, пока не будет добавлен элемент управления во время выполнения.  
  
#### <a name="to-show-the-actions-pane"></a>Чтобы отобразить панель действий  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши ThisWorkbook.vb или ThisWorkbook.cs и нажмите кнопку **Просмотр кода**.  
  
2.  Создать новый экземпляр пользовательского элемента управления в `ThisWorkbook` класса.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  В <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> обработчик событий `ThisWorkbook`, добавьте элемент управления на панель действий.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно проверить документ, чтобы убедиться, что панель действий открывается при открытии документа, и что элементы управления имеют иерархического отношения.  
  
#### <a name="to-test-your-document"></a>Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Убедитесь, что панель действий становится видимой.  
  
3.  Выберите компанию в поле со списком. Убедитесь, что имя компании в <xref:Microsoft.Office.Tools.Excel.NamedRange> управления и что сведения о продукте, перечислены в <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления.  
  
4.  Выберите разные компании, чтобы проверить имя компании и описание продукта изменяются соответствующим образом.  
  
## <a name="next-steps"></a>Следующие шаги  
 Ниже приводятся некоторые из возможных последующих задач.  
  
-   Привязка данных к элементам управления в Word. Дополнительные сведения см. в разделе [Пошаговое руководство: привязка данных к элементам управления в панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Как: Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  