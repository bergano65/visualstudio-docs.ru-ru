---
title: "Пошаговое руководство: Привязка данных к элементам управления в панели действий Word | Документы Microsoft"
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
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: be9a2b19a8c9c34390a359fd8e3350d6af654fde
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-data-to-controls-on-a-word-actions-pane"></a>Пошаговое руководство. Привязка данных к элементам управления в панели действий Word
  В этом пошаговом руководстве демонстрируется привязка данных к элементам управления в панели действий в Word. Элементы управления показывают отношение «Основной/подробности» между таблицами в базе данных SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание панели действий с элементами управления Windows Forms, которые привязаны к данным.  
  
-   Использование связи главного и подчиненного представлений для отображения данных в элементах управления.  
  
-   Отображение панели действий при открытии приложения.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Доступ к серверу с образцом базы данных "Борей" SQL Server.  
  
-   Разрешения на чтение и запись в базу данных SQL Server.  
  
## <a name="creating-the-project"></a>Создание проекта  
 Первым шагом является создание документа Word.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект документа Word с именем **панель действий Word**. В мастере выберите **создания документа**.  
  
     Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет новый документ Word в конструкторе и добавляет **панель действий Word** проекта **обозревателе решений**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Добавление элементов управления в панели действий  
 В данном пошаговом руководстве требуется элемент управления панели действий, который содержит элементы управления Windows Forms с привязкой к данным. Добавление источника данных в проект, а затем перетащите элементы управления из **источники данных** окна элемент управления панели действий.  
  
#### <a name="to-add-an-actions-pane-control"></a>Чтобы добавить элемент управления панели действий  
  
1.  Выберите **панель действий Word** проекта в **обозревателе решений**.  
  
2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
3.  В **Добавление нового элемента** установите флажок **элемент управления панели действий**, назовите его **ActionsControl**, а затем нажмите кнопку **добавить**.  
  
#### <a name="to-add-a-data-source-to-the-project"></a>Добавление источника данных в проект  
  
1.  Если окно **Источники данных** не отображается, откройте его, выбрав в строке меню пункты **Вид**, **Другие окна**, **Источники данных**.  
  
    > [!NOTE]  
    >  Если **Показать источники данных** не доступен, щелкните документ Word и попробуйте снова.  
  
2.  Нажмите кнопку **добавить новый источник данных** запуск **мастер настройки источника данных**.  
  
3.  Выберите **базы данных** и нажмите кнопку **Далее**.  
  
4.  Выберите подключение данных к базе данных Northwind SQL Server или добавьте новое подключение с помощью **новое подключение** кнопки.  
  
5.  Нажмите кнопку **Далее**.  
  
6.  Удалить параметр, чтобы сохранить подключение, если он установлен, а затем щелкните **Далее**.  
  
7.  Разверните **таблиц** узел в **объектов базы данных** окна.  
  
8.  Установите флажок рядом с **поставщики** и **продуктов** таблиц.  
  
9. Нажмите кнопку **Готово**.  
  
 Мастер добавит **поставщики** таблицы и **продуктов** таблицы, к **источники данных** окна. Он также добавляет типизированный набор данных в проект, который является видимым в **обозревателе решений**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Для добавления элементов управления Windows Forms с привязкой к данным элемента управления панели действий  
  
1.  В **источники данных** окна, разверните **поставщики** таблицы.  
  
2.  Щелкните стрелку раскрывающегося списка в **название компании** , а затем установите **ComboBox**.  
  
3.  Перетащите **CompanyName** из **источники данных** окна элемент управления панели действий.  
  
     Объект <xref:System.Windows.Forms.ComboBox> на элемент управления панели действий создается элемент управления. В то же время <xref:System.Windows.Forms.BindingSource> с именем `SuppliersBindingSource`, адаптер таблиц и <xref:System.Data.DataSet> добавляются в проект в области компонентов.  
  
4.  Выберите `SuppliersBindingNavigator` в **компонент** и нажмите клавишу DELETE. Вы не будете использовать `SuppliersBindingNavigator` в этом пошаговом руководстве.  
  
    > [!NOTE]  
    >  Удаление `SuppliersBindingNavigator` не удаляет весь код, созданный для него. Этот код можно удалить.  
  
5.  Перетащите поле со списком под метку и изменение **размер** свойства **171, 21**.  
  
6.  В **источники данных** окна, разверните **продуктов** таблица, которая является потомком **поставщики** таблицы.  
  
7.  Щелкните стрелку раскрывающегося списка в **ProductName** , а затем установите **ListBox**.  
  
8.  Перетащите **ProductName** элемент управления панели действий.  
  
     Объект <xref:System.Windows.Forms.ListBox> на элемент управления панели действий создается элемент управления. В то же время <xref:System.Windows.Forms.BindingSource> с именем `ProductBindingSource` и адаптер таблицы добавляются в проект в области компонентов.  
  
9. Перетащите поле списка, чтобы оно было под метку и изменение **размер** свойства **171,95**.  
  
10. Перетащите <xref:System.Windows.Forms.Button> из **элементов** панели действий управления и поместите его под полем списка.  
  
11. Щелкните правой кнопкой мыши <xref:System.Windows.Forms.Button>, нажмите кнопку **свойства** в контекстном меню и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**Вставить**|  
    |**Text**|**Вставить**|  
  
12. Изменение размера пользовательского элемента управления для размещения элементов управления.  
  
## <a name="setting-up-the-data-source"></a>Настройка источника данных  
 Настройка источника данных, добавьте код для <xref:System.Windows.Forms.UserControl.Load> события элемента управления панели действий для заполнения элемента управления данными из <xref:System.Data.DataTable>и задайте <xref:System.Windows.Forms.Binding.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A> свойства для каждого элемента управления.  
  
#### <a name="to-load-the-control-with-data"></a>Для загрузки элемента управления данными  
  
1.  В <xref:System.Windows.Forms.UserControl.Load> обработчик событий `ActionsControl` класса, добавьте следующий код.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  В C# необходимо присоединить обработчик событий к <xref:System.Windows.Forms.UserControl.Load> событий. Можно заменить этот код в `ActionsControl` конструктор после вызова `InitializeComponent`. Дополнительные сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
#### <a name="to-set-data-binding-properties-of-the-controls"></a>Чтобы задать свойства привязки данных элементов управления  
  
1.  Выберите элемент управления `CompanyNameComboBox`.  
  
2.  В **свойства** окно, нажмите кнопку справа от **DataSource** , а затем выберите **suppliersBindingSource**.  
  
3.  Нажмите кнопку справа от **DisplayMember** , а затем выберите **CompanyName**.  
  
4.  Разверните **DataBindings** свойства, нажмите кнопку справа от **текст** , а затем выберите **нет**.  
  
5.  Выберите элемент управления `ProductNameListBox`.  
  
6.  В **свойства** окно, нажмите кнопку справа от **DataSource** , а затем выберите **productsBindingSource**.  
  
7.  Нажмите кнопку справа от **DisplayMember** , а затем выберите **ProductName**.  
  
8.  Разверните **DataBindings** свойства, нажмите кнопку справа от **SelectedValue** , а затем выберите **нет**.  
  
## <a name="adding-a-method-to-insert-data-into-a-table"></a>Добавление метода для вставки данных в таблицу  
 Следующей задачей является чтение данных из связанных элементов управления и заполнение таблицы в документе Word. Во-первых, создайте процедуру для форматирования заголовков таблицы, а затем добавьте `AddData` метод для создания и форматирования таблицы Word.  
  
#### <a name="to-format-the-table-headings"></a>Форматирование заголовков таблицы  
  
1.  В `ActionsControl` класса, создайте метод для форматирования заголовков таблицы.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
#### <a name="to-create-the-table"></a>Для создания таблицы  
  
1.  В `ActionsControl` класса, написать метод, который создаст таблицу, если он еще не существует и добавить в таблицу данные из области действия.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
#### <a name="to-insert-text-into-a-word-table"></a>Вставка текста в таблицы Word  
  
1.  Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий **вставить** кнопки.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  В C# необходимо создать обработчик событий для <xref:System.Windows.Forms.Control.Click> события кнопки.  Можно заменить этот код в <xref:System.Windows.Forms.UserControl.Load> обработчик событий `ActionsControl` класса.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="showing-the-actions-pane"></a>Отображение панели действий  
 Панель действий становится видимой, если к нему добавляются элементы управления.  
  
#### <a name="to-show-the-actions-pane"></a>Чтобы отобразить панель действий  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **ThisDocument.vb** или **ThisDocument.cs**, а затем нажмите кнопку **Просмотр кода** в контекстном меню.  
  
2.  Создать новый экземпляр элемента управления в верхней части `ThisDocument` класса, чтобы он выглядел как в следующем примере.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Добавьте код для <xref:Microsoft.Office.Tools.Word.Document.Startup> обработчик событий `ThisDocument` таким образом, как в следующем примере.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно проверить документ, чтобы убедиться, что панель действий отображается при открытии документа. Проверку наличия связи главного и подчиненного представлений в элементах управления в панели действий и убедитесь, что слово заполняется данными таблицу при **вставить** кнопки.  
  
#### <a name="to-test-your-document"></a>Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Убедитесь, что панель действий становится видимой.  
  
3.  Выберите название компании в поле со списком и убедитесь, что элементы в **продуктов** списка изменяется.  
  
4.  Выберите продукт, нажмите кнопку **вставить** на панели действий и убедитесь, что в таблицу Word добавляются сведения о продукте.  
  
5.  Добавьте продукты от различных компаний.  
  
## <a name="next-steps"></a>Следующие шаги  
 В этом пошаговом руководстве описываются основные принципы привязки данных к элементам управления в панели действий в Word. Ниже приводятся некоторые из возможных последующих задач.  
  
-   Привязка данных к элементам управления в Excel. Дополнительные сведения см. в разделе [Пошаговое руководство: привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  