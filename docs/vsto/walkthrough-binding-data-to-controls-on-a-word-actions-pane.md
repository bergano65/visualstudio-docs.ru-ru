---
title: "Пошаговое руководство. Привязка данных к элементам управления в панели действий Word"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "панели действий [разработка решений Office в Visual Studio], привязка элементов управления"
  - "панели действий [разработка решений Office в Visual Studio], привязка данных"
  - "элементы управления [разработка решений Office в Visual Studio], привязка данных"
  - "привязка данных [разработка решений Office в Visual Studio], панели действий"
  - "привязка данных [разработка решений Office в Visual Studio], смарт-документы"
  - "смарт-документы [разработка решений Office в Visual Studio], привязка данных"
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Пошаговое руководство. Привязка данных к элементам управления в панели действий Word
  В этом пошаговом руководстве демонстрируется привязка данных к элементам управления на панели действий в слове.  Эти элементы управления отражают отношение "общее\/подробное" между таблицами в базе данных SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   создание панели действий с элементами управления Windows Forms, которые привязаны к данным;  
  
-   использование связи "основной\/подробности" для отображения данных в элементах управления;  
  
-   отображение панели действий при открытии приложения.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях.  Эти элементы определяются используемым выпуском Visual Studio и его параметрами.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Доступ к серверу с примером базы данных "Northwind" SQL Server.  
  
-   Разрешения на чтение из базы данных SQL Server и запись в нее.  
  
## Создание проекта  
 Сначала следует создать проект документа Word.  
  
#### Создание нового проекта  
  
1.  Создайте проект документа Word с именем Панель действий Word.  Выберите в мастере **Создать новый документ**.  
  
     Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет новый документ Word в режиме конструктора и добавит проект **Панель действий Word** в **Обозреватель решений**.  
  
## Добавление элементов управления на панель действий  
 Для выполнения данного пошагового руководства необходим элемент управления панели действий, содержащий элементы управления Windows Forms, которые привязаны к данным.  Добавьте в проект источник данных и затем перетащите элементы управления из окна **Источники данных** в элемент управления панели данных.  
  
#### Добавление элемента управления панели действий  
  
1.  Выберите в **обозревателе решений** проект **Панель действий Word**.  
  
2.  В меню **Проект** выберите команду **Добавить новый элемент**.  
  
3.  В диалоговом окне **Добавление нового элемента** выберите **Элемент управления панели действий**, присвойте файлу имя **ActionsControl** и нажмите кнопку **Добавить**.  
  
#### Добавление источника данных к проекту  
  
1.  Если окно **Источники данных** не отображается, его отображение в строке меню, выбирая **Вид**, **Другие окна**, **Источники данных**.  
  
    > [!NOTE]  
    >  Если пункт **Показать источники данных** недоступен, щелкните документ Word и попробуйте снова.  
  
2.  Выберите команду **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.  
  
3.  Выберите **База данных** и нажмите **Далее**.  
  
4.  Выберите подключение к базе данных SQL Server "Northwind" или добавьте новое подключение с помощью кнопки **Новое подключение**.  
  
5.  Нажмите кнопку **Далее**.  
  
6.  Чтобы сохранить подключение, снимите флажок, если он установлен, и нажмите **Далее**.  
  
7.  В окне **Объекты базы данных** разверните узел **Таблицы**.  
  
8.  Установите флажки возле таблиц **Поставщики** и **Продукты**.  
  
9. Нажмите кнопку **Готово**.  
  
 Мастер добавит таблицы **Поставщики** и **Продукты** в окно **Источники данных**.  Также к проекту добавляется типизированный набор данных, который отображается в **Обозревателе решений**.  
  
#### Добавление привязанных к данным элементов управления Windows Forms в элемент управления панели действий  
  
1.  Разверните таблицу **Поставщики** в окне **Источники данных**.  
  
2.  Щелкните стрелку вниз на узле **Название компании** и выберите пункт **ComboBox**.  
  
3.  Из окна **Источники данных** перетащите узел **CompanyName** на элемент управления панели действий.  
  
     На элементе управления панели действий создается элемент управления <xref:System.Windows.Forms.ComboBox>.  Одновременно в область компонентов проекта добавляются элемент управления <xref:System.Windows.Forms.BindingSource> с именем `SuppliersBindingSource`, адаптер таблиц и экземпляр класса <xref:System.Data.DataSet>.  
  
4.  В области **Компоненты** выберите объект `SuppliersBindingNavigator` и нажмите клавишу DELETE.  В данном примере объект `SuppliersBindingNavigator` использоваться не будет.  
  
    > [!NOTE]  
    >  При удалении объекта `SuppliersBindingNavigator` код, созданный для него, не удаляется.  Этот код можно удалить.  
  
5.  Перетащите поле со списком под метку и присвойте свойству **Size** значение 171, 21.  
  
6.  В окне **Источники данных** разверните таблицу **Продукты**, являющуюся дочерней таблицей таблицы **Поставщики**.  
  
7.  Щелкните стрелку вниз на узле **ProductName** и выберите пункт **ListBox**.  
  
8.  Перетащите **ProductName** на элемент управления панели действий.  
  
     На элементе управления панели действий создается элемент управления <xref:System.Windows.Forms.ListBox>.  Одновременно в область компонентов проекта добавляются элемент управления <xref:System.Windows.Forms.BindingSource> с именем `ProductBindingSource` и адаптер таблиц.  
  
9. Перетащите поле списка под метку и присвойте свойству **Size** значение 171,95.  
  
10. Перетащите из **Панели элементов** экземпляр <xref:System.Windows.Forms.Button> на элемент управления панели действий и поместите его под полем списка.  
  
11. Щелкните правой кнопкой мыши элемент управления <xref:System.Windows.Forms.Button>, выберите в контекстном меню пункт **Свойства** и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**Атрибут Insert**|  
    |**Текст.**|**Атрибут Insert**|  
  
12. Измените размер пользовательского элемента управления в соответствии с размерами элементов управления.  
  
## Настройка источника данных  
 Чтобы настроить источник данных, добавьте код в обработчик событий <xref:System.Windows.Forms.UserControl.Load> элемента управления панели действий для заполнения элемента управления данными из объекта <xref:System.Data.DataTable>, а также задайте свойства <xref:System.Windows.Forms.Binding.DataSource%2A> и <xref:System.Windows.Forms.BindingSource.DataMember%2A> для каждого элемента управления.  
  
#### Заполнение элемента управления данными  
  
1.  Добавьте следующий код в обработчик событий <xref:System.Windows.Forms.UserControl.Load> класса `ActionsControl`:  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#1)]  
  
2.  В C\# следует присоединить обработчик событий к событию <xref:System.Windows.Forms.UserControl.Load>.  Этот код можно поместить в конструктор `ActionsControl` после обращения к `InitializeComponent`.  Дополнительные сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#33)]  
  
#### Установка свойств привязки данных элементов управления  
  
1.  Выберите элемент управления `CompanyNameComboBox`.  
  
2.  В окне **Свойства** нажмите кнопку справа от свойства **DataSource** и выберите **suppliersBindingSource**.  
  
3.  Нажмите кнопку справа от свойства **DisplayMember** и выберите **CompanyName**.  
  
4.  Разверните свойство **DataBindings**, нажмите кнопку справа от свойства **Text** и выберите **None**.  
  
5.  Выберите элемент управления `ProductNameListBox`.  
  
6.  В окне **Свойства** нажмите кнопку справа от свойства **DataSource** и выберите **productsBindingSource**.  
  
7.  Нажмите кнопку справа от свойства **DisplayMember** и выберите **ProductName**.  
  
8.  Разверните свойство **DataBindings**, нажмите кнопку справа от свойства **SelectedValue** и выберите **None**.  
  
## Добавление метода для вставки данных в таблицу  
 Следующей задачей является чтение данных из связанных элементов управления и заполнение таблицы в документе Word.  Сперва следует создать процедуру для форматирования заголовков таблицы, а затем добавить метод `AddData` для создания и форматирования таблицы Word.  
  
#### Форматирование заголовков таблицы  
  
1.  В классе `ActionsControl` создайте метод для форматирования заголовков таблицы.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#2)]
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#2)]  
  
#### Создание таблицы  
  
1.  В классе `ActionsControl` создайте метод для создания таблицы, если она еще не создана, и добавления в нее данных из панели действий.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#3)]  
  
#### Вставка текста в таблицу Word  
  
1.  В обработчик событий <xref:System.Windows.Forms.Control.Click> кнопки **Insert** добавьте следующий код:  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#4)]  
  
2.  В C\# необходимо создать обработчик событий <xref:System.Windows.Forms.Control.Click> кнопки.  Этот код можно поместить в обработчик событий <xref:System.Windows.Forms.UserControl.Load> класса `ActionsControl`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#5)]  
  
## Отображение панели действий  
 Панель действий отображается после добавления на нее элементов управления.  
  
#### Отображение панели действий  
  
1.  В **обозревателе решений** щелкните правой кнопкой мыши **ThisDocument.vb** или **ThisDocument.cs** и выберите в контекстном меню команду **Перейти к коду**.  
  
2.  Создайте новый экземпляр элемента управления в начале класса `ThisDocument`, как показано в следующем примере:  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#6)]  
  
3.  Добавьте код в обработчик событий <xref:Microsoft.Office.Tools.Word.Document.Startup> класса `ThisDocument`, чтобы он выглядел следующим образом:  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
## Тестирование приложения  
 Теперь можно протестировать документ, чтобы проверить, что при его открытии отображается панель действий.  Проверьте отношение "основной\/подробности" в элементах управления в панели действий и убедитесь, что таблица Word заполняется данными при нажатии кнопки **Вставить**.  
  
#### Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Убедитесь, что панель действий отображается.  
  
3.  Выберите название компании в поле со списком и убедитесь, что содержимое списка **Продукты** изменяется.  
  
4.  Выберите название продукта, нажмите кнопку **Вставить** в панели действий и убедитесь, что в таблицу Word добавляются сведения о продукте.  
  
5.  Добавьте продукты от различных компаний.  
  
## Следующие действия  
 В этом пошаговом руководстве рассматриваются основные принципы привязки данных к элементам управления в панели действий Microsoft Office Word.  Далее будут рассмотрены следующие задачи:  
  
-   Привязка данных к элементам управления в Excel.  Дополнительные сведения см. в разделе [Пошаговое руководство. Привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Развертывание проекта.  Дополнительные сведения см. в разделе [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Практическое руководство. Добавление области действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  