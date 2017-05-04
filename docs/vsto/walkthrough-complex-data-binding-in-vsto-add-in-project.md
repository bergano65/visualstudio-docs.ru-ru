---
title: "Пошаговое руководство. Сложная привязка данных в проекте надстройки VSTO | Microsoft Docs"
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
  - "привязка данных [разработка решений Office в Visual Studio], Excel"
  - "данные [разработка решений Office в Visual Studio], привязка данных"
  - "сложные данные [разработка решений Office в Visual Studio]"
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Пошаговое руководство. Сложная привязка данных в проекте надстройки VSTO
  В проектах надстроек VSTO можно привязывать данные к элементам управления ведущего приложения и элементам управления Windows Forms. В этом пошаговом руководстве демонстрируется добавление элементов управления на лист Microsoft Office Excel и привязка элементов управления к данным во время выполнения.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   добавление элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> на лист во время выполнения;  
  
-   создание объекта <xref:System.Windows.Forms.BindingSource>, соединяющего элемент управления с экземпляром набора данных.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Доступ к запущенному экземпляру SQL Server 2005 или SQL Server 2005 Express с подключенной учебной базой данных `AdventureWorksLT`. Базу данных `AdventureWorksLT` можно скачать с [веб\-сайта CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Дополнительные сведения о подключении базы данных см. в следующих разделах:  
  
    -   Сведения о подключении базы данных с помощью SQL Server Management Studio или SQL Server Management Studio Express см. в разделе [Присоединение базы данных \(SQL Server Management Studio\)](http://msdn.microsoft.com/ru-ru/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Сведения о подключении базы данных с помощью командной строки см. в разделе [Как добавить файл базы данных к SQL Server Express](http://msdn.microsoft.com/ru-ru/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Создание нового проекта  
 Первым шагом является создание проекта надстройки VSTO для Excel.  
  
#### Создание нового проекта  
  
1.  Создайте проект надстройки VSTO для Excel с именем **Заполнение листов из базы данных** в Visual Basic или C\#.  
  
     Для получения дополнительной информации см. [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     В Visual Studio откроется файл `ThisAddIn.vb` или `ThisAddIn.cs` и будет добавлен проект **Заполнение листов из базы данных** в **обозреватель решений**.  
  
## Создание источника данных  
 С помощью окна **Источники данных** добавьте типизированный набор данных в свой проект.  
  
#### Добавление типизированного набора данных в проект  
  
1.  Если окно **Источники данных** не отображается, откройте его, выбрав в строке меню пункты **Вид**, **Другие окна**, **Источники данных**.  
  
2.  Выберите команду **Добавить новый источник данных**, чтобы запустить **Мастер настройки источника данных**.  
  
3.  Щелкните **База данных** и нажмите кнопку **Далее**.  
  
4.  Если подключение к базе данных `AdventureWorksLT` существует, выберите его и нажмите кнопку **Далее**.  
  
     В противном случае нажмите **Создать подключение** и в диалоговом окне **Добавление подключения**  создайте новое подключение. Дополнительные сведения см. в разделе [Практическое руководство. Подключение к данным в базе данных](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
5.  На странице **Сохранение подключения в файле конфигурации приложения** нажмите кнопку **Далее**.  
  
6.  На странице **Выбор объектов базы данных** разверните узел **Таблицы** и выберите таблицу **Address \(SalesLT\)**.  
  
7.  Нажмите кнопку **Готово**.  
  
     Файл AdventureWorksLTDataSet.xsd добавится в **обозреватель решений**. В этом файле определены следующие элементы:  
  
    -   Типизированный набор данных с именем `AdventureWorksLTDataSet`. Этот набор данных представляет содержимое таблицы **Address \(SalesLT\)** в базе данных AdventureWorksLT.  
  
    -   TableAdapter с именем `AddressTableAdapter`. Этот адаптер TableAdapter может использоваться для чтения и записи данных в `AdventureWorksLTDataSet`. Для получения дополнительной информации см. [Общие сведения об адаптере таблиц](/visual-studio/data-tools/tableadapter-overview).  
  
     Далее в пошаговом руководстве используются оба эти объекта.  
  
## Создание элементов управления и их привязка к данным  
 В этом пошаговом руководстве элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> отображает все выбранные данные из таблицы сразу после того, как пользователь открывает книгу. Объект списка использует <xref:System.Windows.Forms.BindingSource> для подключения элемента управления к базе данных.  
  
 Дополнительные сведения о привязке элементов управления к данным см. в разделе [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Добавление объекта списка, набора данных и адаптера таблиц  
  
1.  В классе `ThisAddIn` объявите приведенные ниже элементы управления для отображения таблицы `Address` из набора данных `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  В метод `ThisAddIn_Startup` добавьте приведенный ниже код для инициализации набора данных и его заполнения сведениями из набора данных `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  Добавьте следующий код в метод `ThisAddIn_Startup`. Этот код создает ведущий элемент, расширяющий лист. Дополнительные сведения см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  Создайте диапазон и добавьте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  Свяжите объект списка с `AdventureWorksLTDataSet`, используя объект <xref:System.Windows.Forms.BindingSource>. Передайте имена столбцов, которые следует привязать к объекту списка.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#5)]  
  
## Тестирование надстройки  
 После запуска Excel элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> отображает данные из таблицы `Address` набора данных `AdventureWorksLTDataSet`.  
  
#### Тестирование надстройки VSTO  
  
-   Нажмите клавишу **F5**.  
  
     Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `addressListObject` создается на листе. Одновременно в проект добавляется объект набора данных `adventureWorksLTDataSet` и объект <xref:System.Windows.Forms.BindingSource> с именем `addressBindingSource`. Объект <xref:Microsoft.Office.Tools.Excel.ListObject> привязан к объекту <xref:System.Windows.Forms.BindingSource>, который в свою очередь привязан к объекту набора данных.  
  
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
 [Общие сведения об использовании файлов локальной базы данных в решениях для Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Подключение к данным в приложениях Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Общие сведения о компоненте BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  