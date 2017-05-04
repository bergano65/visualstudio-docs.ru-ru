---
title: "Пошаговое руководство. Простая привязка данных в проекте надстройки VSTO | Microsoft Docs"
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
  - "данные [разработка решений Office в Visual Studio], привязка данных"
  - "привязка данных [разработка решений Office в Visual Studio], Word"
  - "данные [разработка решений Office в Visual Studio], простая привязка данных"
ms.assetid: b248d194-a8b1-4f87-94c4-24e940eea1fd
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Пошаговое руководство. Простая привязка данных в проекте надстройки VSTO
  В проектах надстроек VSTO можно привязывать данные к элементам управления ведущего приложения и элементам управления Windows Forms. В этом пошаговом руководстве демонстрируется добавление элементов управления в документ Microsoft Office Word и привязка элементов управления к данным во время выполнения.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Добавление <xref:Microsoft.Office.Tools.Word.ContentControl> в документ во время выполнения.  
  
-   Создание объекта <xref:System.Windows.Forms.BindingSource>, подключающего элемент управления к экземпляру набора данных.  
  
-   Предоставление пользователю возможности прокручивать записи и просматривать их в элементе управления.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Доступ к запущенному экземпляру SQL Server 2005 или SQL Server 2005 Express с подключенной учебной базой данных `AdventureWorksLT`. Базу данных `AdventureWorksLT` можно загрузить с [веб\-сайта CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Дополнительные сведения о подключении базы данных см. в следующих разделах.  
  
    -   Сведения о подключении базы данных с помощью SQL Server Management Studio или SQL Server Management Studio Express см. в разделе [Практическое руководство. Подключение базы данных \(SQL Server Management Studio\)](http://msdn.microsoft.com/ru-ru/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Сведения о подключении базы данных с помощью командной строки см. в разделе [Практическое руководство. Подключение файла базы данных к SQL Server Express](http://msdn.microsoft.com/ru-ru/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Создание нового проекта  
 Первым шагом является создание проекта надстройки Word VSTO.  
  
#### Создание нового проекта  
  
1.  Создайте проект надстройки VSTO для Word с именем **Заполнение документов из базы данных** в Visual Basic или C\#.  
  
     Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio открывает файл ThisAddIn.vb или ThisAddIn.cs и добавляет проект **Заполнение документов из базы данных** в **обозреватель решений**.  
  
2.  Если проект предназначен для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], добавьте ссылку на сборку Microsoft.Office.Tools.Word.v4.0.Utilities.dll. Эта ссылка потребуется для программного добавления элемента управления Windows Forms в документ далее в этом пошаговом руководстве.  
  
## Создание источника данных  
 С помощью окна **Источники данных** добавьте типизированный набор данных в свой проект.  
  
#### Добавление типизированного набора данных в проект  
  
1.  Если окно **Источники данных** не отображается, откройте его, выбрав в строке меню пункты **Вид**, **Другие окна**, **Источники данных**.  
  
2.  Выберите команду **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.  
  
3.  Щелкните **База данных** и нажмите кнопку **Далее**.  
  
4.  Если подключение к базе данных `AdventureWorksLT` существует, выберите его и нажмите кнопку **Далее**.  
  
     В противном случае нажмите **Создать подключение** и в диалоговом окне **Добавление подключения**  создайте новое подключение. Для получения дополнительной информации см. [Практическое руководство. Подключение к данным в базе данных](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
5.  На странице **Сохранение подключения в файле конфигурации приложения** нажмите кнопку **Далее**.  
  
6.  На странице **Выбор объектов базы данных** разверните узел **Таблицы** и выберите таблицу **Customer \(SalesLT\)**.  
  
7.  Нажмите кнопку **Готово**.  
  
     Файл AdventureWorksLTDataSet.xsd добавится в **обозреватель решений**. Этот файл определяет следующие элементы.  
  
    -   Типизированный набор данных с именем `AdventureWorksLTDataSet`. Этот набор данных представляет содержимое таблицы **Customer \(SalesLT\)** в базе данных AdventureWorksLT.  
  
    -   TableAdapter с именем `CustomerTableAdapter`. Этот адаптер TableAdapter может использоваться для чтения и записи данных в `AdventureWorksLTDataSet`. Для получения дополнительной информации см. [Общие сведения об адаптере таблиц](/visual-studio/data-tools/tableadapter-overview).  
  
     Далее в этом пошаговом руководстве используются оба эти объекта.  
  
## Создание элементов управления и их привязка к данным  
 Интерфейс для просмотра записей базы данных в этом пошаговом руководстве является очень простым и создается прямо внутри документа. Один элемент управления <xref:Microsoft.Office.Tools.Word.ContentControl> отображает по одной записи базы данных, а второй элемент управления <xref:Microsoft.Office.Tools.Word.Controls.Button> позволяет прокручивать записи вперед и назад. Элемент управления содержимым использует <xref:System.Windows.Forms.BindingSource> для подключения к базе данных.  
  
 Дополнительные сведения о привязке элементов управления к данным см. в разделе [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Создание интерфейса в документе  
  
1.  В классе `ThisAddIn` объявите следующие элементы управления для отображения и прокрутки таблицы `Customer` из базы данных `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_WordAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  В метод `ThisAddIn_Startup` добавьте приведенный ниже код для инициализации набора данных и его заполнения сведениями из базы данных `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_WordAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  Добавьте следующий код в метод `ThisAddIn_Startup`. Этот код создает ведущий элемент, расширяющий документ. Для получения дополнительной информации см. [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_WordAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  Определите несколько диапазонов в начале документа. Эти диапазоны указывают место вставки текста и размещения элементов управления.  
  
     [!code-csharp[Trin_WordAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  Добавьте элементы управления интерфейса в ранее определенные диапазоны.  
  
     [!code-csharp[Trin_WordAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#5)]  
  
6.  Привяжите элемент управления содержимым к `AdventureWorksLTDataSet` с помощью <xref:System.Windows.Forms.BindingSource>. Разработчикам C\# следует добавить два обработчика событий для элементов управления <xref:Microsoft.Office.Tools.Word.Controls.Button>.  
  
     [!code-csharp[Trin_WordAddInDatabase#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddInDatabase#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#6)]  
  
7.  Добавьте следующий код для перемещения по записям базы данных.  
  
     [!code-csharp[Trin_WordAddInDatabase#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDatabase#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#7)]  
  
## Тестирование надстройки  
 При открытии Word элемент управления содержимым отображает данные из набора данных `AdventureWorksLTDataSet`. Прокрутите записи базы данных, нажимая кнопки **Далее** и **Назад**.  
  
#### Тестирование надстройки VSTO  
  
1.  Нажмите клавишу **F5**.  
  
     Элемент управления содержимым с именем `customerContentControl` создается и заполняется данными. В то же время в проект добавляется объект набора данных с именем `adventureWorksLTDataSet` и объект <xref:System.Windows.Forms.BindingSource> с именем `customerBindingSource`. Объект <xref:Microsoft.Office.Tools.Word.ContentControl> привязан к объекту <xref:System.Windows.Forms.BindingSource>, который в свою очередь привязан к объекту набора данных.  
  
2.  Нажимайте кнопки **Далее** и **Назад**, чтобы прокрутить записи базы данных.  
  
## См. также  
 [Данные в решениях Office](../vsto/data-in-office-solutions.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Практическое руководство. Заполнение листов данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Практическое руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Практическое руководство. Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Практическое руководство. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Практическое руководство. Прокрутка записей базы данных на листе](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Пошаговое руководство. Простая привязка данных в проекте уровня документа](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Пошаговое руководство. Сложная привязка данных в проекте уровня документа](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Общие сведения об использовании файлов локальной базы данных в решениях для Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Общие сведения об источниках данных](../data-tools/add-new-data-sources.md)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Практическое руководство. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Общие сведения об использовании файлов локальной базы данных в решениях для Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Подключение к данным в приложениях Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Общие сведения о компоненте BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
  