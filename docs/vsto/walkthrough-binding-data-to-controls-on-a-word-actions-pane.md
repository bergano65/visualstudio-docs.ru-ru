---
title: 'Пошаговое руководство: Привязка данных к элементам управления в панели действий Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 17daf186920be45a70200cd896a390ab74c4c6d0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873894"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Пошаговое руководство: Привязка данных к элементам управления в панели действий Word
  В этом пошаговом руководстве демонстрируется привязка данных к элементам управления в панели действий в Word. Элементы управления показывают отношение «Основной/подробности» между таблицами в базе данных SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание панели действий с элементами управления Windows Forms, которые привязаны к данным.  
  
-   Использование отношение "основной/подробности" для отображения данных в элементах управления.  
  
-   Отображение панели действий при открытии приложения.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Доступ к серверу с образцом базы данных "Борей" SQL Server.  
  
-   Разрешения на чтение и запись к базе данных SQL Server.  
  
## <a name="create-the-project"></a>Создание проекта  
 Первым шагом является создание документа Word.  
  
### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект документа Word с именем **панель действий Word**. В мастере выберите **создания документа**.  
  
     Дополнительные сведения см. в разделе [как: проектов Office, создайте в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio открывает новый документ Word в конструкторе и добавляет **панель действий Word** проект **обозревателе решений**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Добавление элементов управления в панели действий  
 В этом пошаговом руководстве необходимо, чтобы элемент управления панели действий, который содержит элементы управления Windows Forms с привязкой к данным. Добавить источник данных к проекту, а затем перетащите элементы управления из **источников данных** окна для элемента управления панели действий.  
  
### <a name="to-add-an-actions-pane-control"></a>Чтобы добавить элемент управления панели действий  
  
1.  Выберите **панель действий Word** в проекте **обозревателе решений**.  
  
2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
3.  В **Добавление нового элемента** выберите **элемента управления панели действий**, назовите его **ActionsControl**, а затем нажмите кнопку **добавить**.  
  
### <a name="to-add-a-data-source-to-the-project"></a>Добавление источника данных в проект  
  
1. Если **источников данных** окно не отображается, откройте его в строке меню выберите **представление** > **Other Windows**  >   **Источники данных**.  
  
   > [!NOTE]  
   >  Если **Показать источники данных** недоступен, щелкните документ Word и попробуйте снова.  
  
2. Нажмите кнопку **добавить новый источник данных** запустить **мастер настройки источника данных**.  
  
3. Выберите **базы данных** и нажмите кнопку **Далее**.  
  
4. Выберите подключение данных к базе данных SQL Server Northwind или добавьте новое подключение с помощью **новое подключение** кнопки.  
  
5. Нажмите кнопку **Далее**.  
  
6. Очистить параметр, чтобы сохранить подключение, если он выбран, а затем нажмите кнопку **Далее**.  
  
7. Разверните **таблиц** узел в **объектов базы данных** окна.  
  
8. Установите флажок рядом с полем **поставщики** и **продуктов** таблиц.  
  
9. Нажмите кнопку **Готово**.  
  
   Мастер добавляет **поставщики** таблицы и **продуктов** таблицы **источников данных** окна. Он также добавляет типизированный набор данных в проект, который является видимым в **обозревателе решений**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Для добавления элементов управления Windows Forms с привязкой к данным элемента управления панели действий  
  
1.  В **источников данных** окне разверните **поставщики** таблицы.  
  
2.  Щелкните стрелку раскрывающегося списка в **название компании** узел и выберите **ComboBox**.  
  
3.  Перетащите **CompanyName** из **источников данных** окна для элемента управления панели действий.  
  
     Объект <xref:System.Windows.Forms.ComboBox> создается элемент управления на панель действий. В то же время <xref:System.Windows.Forms.BindingSource> с именем `SuppliersBindingSource`, адаптер таблицы и <xref:System.Data.DataSet> добавляются в проект в области компонентов.  
  
4.  Выберите `SuppliersBindingNavigator` в **компонент** и нажмите клавишу **удалить**. Вы не будете использовать `SuppliersBindingNavigator` в этом пошаговом руководстве.  
  
    > [!NOTE]  
    >  Удаление `SuppliersBindingNavigator` не удаляет весь код, который был создан для него. Этот код можно удалить.  
  
5.  Перетащите поле со списком под меткой и изменение **размер** свойства **171, 21**.  
  
6.  В **источников данных** окне разверните **продуктов** таблица, которая является потомком **поставщики** таблицы.  
  
7.  Щелкните стрелку раскрывающегося списка в **ProductName** узел и выберите **ListBox**.  
  
8.  Перетащите **ProductName** для элемента управления панели действий.  
  
     Объект <xref:System.Windows.Forms.ListBox> создается элемент управления на панель действий. В то же время <xref:System.Windows.Forms.BindingSource> с именем `ProductBindingSource` и адаптер таблицы добавляются в проект в области компонентов.  
  
9. Переместите поле со списком, таким образом, чтобы под меткой и изменение **размер** свойства **171,95**.  
  
10. Перетащите <xref:System.Windows.Forms.Button> из **элементов** панели действий управления и поместите его под поле со списком.  
  
11. Щелкните правой кнопкой мыши <xref:System.Windows.Forms.Button>, нажмите кнопку **свойства** в контекстном меню и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**Вставить**|  
    |**Text**|**Вставить**|  
  
12. Измените размер пользовательского элемента управления для размещения элементов управления.  
  
## <a name="set-up-the-data-source"></a>Настройка источника данных  
 Чтобы настроить источник данных, добавьте код для <xref:System.Windows.Forms.UserControl.Load> событий элемента управления панели действий для заполнения элемента управления данными из <xref:System.Data.DataTable>и задайте <xref:System.Windows.Forms.Binding.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A> свойства для каждого элемента управления.  
  
### <a name="to-load-the-control-with-data"></a>Для загрузки элемента управления данными  
  
1.  В <xref:System.Windows.Forms.UserControl.Load> обработчик событий `ActionsControl` класса, добавьте следующий код.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  В C# необходимо присоединить обработчик событий, <xref:System.Windows.Forms.UserControl.Load> событий. Можно поместить этот код в `ActionsControl` конструктора после вызова `InitializeComponent`. Дополнительные сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
### <a name="to-set-data-binding-properties-of-the-controls"></a>Чтобы задать свойства привязки данных элементов управления  
  
1.  Выберите элемент управления `CompanyNameComboBox`.  
  
2.  В **свойства** окно, нажмите кнопку справа от **DataSource** свойства, а затем выберите **suppliersBindingSource**.  
  
3.  Нажмите кнопку справа от **DisplayMember** свойства, а затем выберите **CompanyName**.  
  
4.  Разверните **DataBindings** свойство, нажмите кнопку справа от **текст** свойства, а затем выберите **None**.  
  
5.  Выберите элемент управления `ProductNameListBox`.  
  
6.  В **свойства** окно, нажмите кнопку справа от **DataSource** свойства, а затем выберите **productsBindingSource**.  
  
7.  Нажмите кнопку справа от **DisplayMember** свойства, а затем выберите **ProductName**.  
  
8.  Разверните **DataBindings** свойство, нажмите кнопку справа от **SelectedValue** свойства, а затем выберите **None**.  
  
## <a name="add-a-method-to-insert-data-into-a-table"></a>Добавление метода для вставки данных в таблицу  
 Следующая задача — для чтения данных из связанных элементов управления и заполнение таблицы в документе Word. Во-первых, создайте процедуру для форматирования заголовков таблицы, а затем добавьте `AddData` метод для создания и форматирования таблицы Word.  
  
### <a name="to-format-the-table-headings"></a>Форматирование заголовков таблицы  
  
1.  В `ActionsControl` создайте метод для форматирования заголовков таблицы.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
### <a name="to-create-the-table"></a>Чтобы создать таблицу  
  
1.  В `ActionsControl` класса, написание метода, который создаст таблицу, если один еще не существует и добавить данные из области действия в таблице.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
### <a name="to-insert-text-into-a-word-table"></a>Для вставки текста в таблицу Word  
  
1.  Добавьте следующий код, чтобы <xref:System.Windows.Forms.Control.Click> обработчик событий **вставить** кнопки.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  В C#, необходимо создать обработчик событий для <xref:System.Windows.Forms.Control.Click> события кнопки.  Можно поместить этот код в <xref:System.Windows.Forms.UserControl.Load> обработчик событий `ActionsControl` класса.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="show-the-actions-pane"></a>Показать панель действий  
 Панель действий становится видимой, после добавления элементов управления к нему.  
  
### <a name="to-show-the-actions-pane"></a>Чтобы отобразить панель действий  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **ThisDocument.vb** или **ThisDocument.cs**, а затем нажмите кнопку **просмотреть код** в контекстном меню.  
  
2.  Создать новый экземпляр элемента управления в верхней части `ThisDocument` класса, чтобы он выглядел, как в следующем примере.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Добавьте код для <xref:Microsoft.Office.Tools.Word.Document.Startup> обработчик событий `ThisDocument` таким образом, как в следующем примере.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="test-the-application"></a>Тестирование приложения  
 Теперь можно проверить документ, чтобы убедиться, что панель действий отображается при открытии документа. Тестирования для отношения "основной/подробности" в элементах управления на панели действий и убедитесь, что данные заполняются слов в таблице, когда **вставить** кнопки.  
  
### <a name="to-test-your-document"></a>Проверка документа  
  
1.  Нажмите клавишу **F5** для запуска проекта.  
  
2.  Убедитесь, что панель действий является видимым.  
  
3.  Выберите название компании в поле со списком и убедитесь, что элементы в **продуктов** списка изменяется.  
  
4.  Выберите продукт, нажмите кнопку **вставить** на панели действий и убедитесь, что сведения о продукте добавляются в таблицу Word.  
  
5.  Вставьте дополнительные продукты от различных компаний.  
  
## <a name="next-steps"></a>Следующие шаги  
 В этом пошаговом руководстве описываются основные принципы привязки данных к элементам управления в панели действий в Word. Ниже приводятся некоторые из возможных последующих задач.  
  
-   Привязка данных к элементам управления в Excel. Дополнительные сведения см. в разделе [Пошаговое руководство: привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Практическое: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  