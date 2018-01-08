---
title: ": Пошаговое | Документы Microsoft"
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
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: "58"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 36053a8ef415e35f1244d0e379a49a46ea24f33d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Пошаговое руководство. Простая привязка данных в проекте уровня документа
  В этом пошаговом руководстве демонстрируются основные принципы привязки данных в проекте уровня документа. Одного поля данных в базе данных SQL Server привязана к именованному диапазону в Microsoft Office Excel. Также показаны способы добавления элементов управления, которые позволяют прокручивать все записи в таблице.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание источника данных для проекта Excel.  
  
-   Добавление элементов управления на лист.  
  
-   Прокрутка записей базы данных.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Доступ к серверу с образцом базы данных "Борей" SQL Server.  
  
-   Разрешения на чтение и запись в базу данных SQL Server.  
  
## <a name="creating-a-new-project"></a>Создание нового проекта  
 На этом шаге вы создадите проект книги Excel.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект книги Excel с именем **простая привязка данных**, с помощью Visual Basic или C#. Убедитесь, что **создания документа** выбран. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio открывает новую книгу Excel в конструкторе и добавляет **простая привязка данных** проекта **обозревателе решений**.  
  
## <a name="creating-the-data-source"></a>Создание источника данных  
 С помощью окна **Источники данных** добавьте типизированный набор данных в свой проект.  
  
#### <a name="to-create-the-data-source"></a>Создание источника данных  
  
1.  Если окно **Источники данных** не отображается, откройте его, выбрав в строке меню пункты **Вид**, **Другие окна**, **Источники данных**.  
  
2.  Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.  
  
3.  Выберите **базы данных** и нажмите кнопку **Далее**.  
  
4.  Выберите подключение данных к базе данных Northwind SQL Server или добавьте новое подключение с использованием **новое подключение** кнопки.  
  
5.  После выбора или создания подключения нажмите кнопку **Далее**.  
  
6.  Удалить параметр, чтобы сохранить подключение, если он установлен, а затем щелкните **Далее**.  
  
7.  Разверните **таблиц** узел в **объектов базы данных** окна.  
  
8.  Установите флажок рядом с **клиентов** таблицы.  
  
9. Нажмите кнопку **Готово**.  
  
 Мастер добавит **клиентов** таблицы, к **источники данных** окна. Он также добавляет типизированный набор данных в проект, который является видимым в **обозревателе решений**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Добавление элементов управления на лист  
 В данном пошаговом руководстве требуется два именованных диапазонов и четыре кнопки на первом листе. Сначала добавьте два именованных диапазона из **источники данных** окна, чтобы они автоматически привязываются к источнику данных. Добавьте кнопки, из **элементов**.  
  
#### <a name="to-add-two-named-ranges"></a>Добавление двух именованных диапазонов  
  
1.  Убедитесь, что **Мой простой Binding.xlsx данных** книга открыта в конструкторе Visual Studio с **Sheet1** отображается.  
  
2.  Откройте **источники данных** окна и разверните **клиентов** узла.  
  
3.  Выберите **CompanyName** столбца и щелкните стрелку раскрывающегося списка, которая появляется.  
  
4.  Выберите **NamedRange** в раскрывающемся списке, а затем перетащите **CompanyName** столбца в ячейку **A1**.  
  
     Объект <xref:Microsoft.Office.Tools.Excel.NamedRange> управления с именем `companyNameNamedRange` создается в ячейке **A1**. В то же время <xref:System.Windows.Forms.BindingSource> с именем `customersBindingSource`, адаптер таблиц и <xref:System.Data.DataSet> экземпляр добавляются в проект. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource>, который, в свою очередь, привязан к <xref:System.Data.DataSet> экземпляра.  
  
5.  Выберите **CustomerID** столбца в **источники данных** окна и щелкните стрелку раскрывающегося списка, которая появляется.  
  
6.  Нажмите кнопку **NamedRange** в раскрывающемся списке, а затем перетащите **CustomerID** столбца в ячейку **B1**.  
  
7.  Другой <xref:Microsoft.Office.Tools.Excel.NamedRange> управления с именем `customerIDNamedRange` создается в ячейке **B1**и привязан к <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-four-buttons"></a>Добавление четырех кнопок  
  
1.  Из **стандартные элементы управления** вкладке **элементов**, добавьте <xref:System.Windows.Forms.Button> управления ячейку **A3** листа.  
  
     Эта кнопка называется `Button1`.  
  
2.  Добавьте еще три кнопки в следующие ячейки в указанном порядке, чтобы имена, как показано:  
  
    |Ячейки|(Имя)|  
    |----------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 Следующий шаг — добавить текст для кнопок, а в C# добавьте обработчики событий.  
  
## <a name="initializing-the-controls"></a>Инициализация элементов управления  
 Задать текст кнопки и добавьте обработчики событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> событий.  
  
#### <a name="to-initialize-the-controls"></a>Инициализация элементов управления  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1.vb** или **Sheet1.cs**, а затем нажмите кнопку **Просмотр кода** в контекстном меню.  
  
2.  Добавьте следующий код в `Sheet1_Startup` метод, чтобы задать текст для каждой кнопки.  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3.  Только в C#, добавьте обработчики событий для кнопки события click `Sheet1_Startup` метод.  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
 Теперь добавьте код для обработки <xref:System.Windows.Forms.Control.Click> этих кнопок, чтобы пользователь может просматривать по записям.  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Добавление кода, чтобы включить прокрутку записей  
 Добавьте код для <xref:System.Windows.Forms.Control.Click> обработчик событий для каждой кнопки для перемещения по записям.  
  
#### <a name="to-move-to-the-first-record"></a>Чтобы перейти к первой записи  
  
1.  Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button1` и добавьте следующий код, чтобы перейти к первой записи:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
#### <a name="to-move-to-the-previous-record"></a>Для перехода к предыдущей записи  
  
1.  Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button2` и добавьте следующий код, чтобы переместить позицию назад на единицу:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
#### <a name="to-move-to-the-next-record"></a>Для перемещения к следующей записи  
  
1.  Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button3` и добавьте следующий код, чтобы переместить позицию на единицу:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
#### <a name="to-move-to-the-last-record"></a>Чтобы перейти к последней записи  
  
1.  Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button4` и добавьте следующий код, чтобы перейти к последней записи:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно протестировать книгу, чтобы убедиться в том, что можно выполнять поиск записей в базе данных.  
  
#### <a name="to-test-your-workbook"></a>Проверка книги  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Убедитесь, что первая запись отображается в ячейках **A1** и **B1**.  
  
3.  Нажмите кнопку  **>**  (`Button3`) кнопку и убедитесь, что следующая запись отображается в ячейке **A1** и **B1**.  
  
4.  Щелкните другие кнопки прокрутки для подтверждения, что записи меняются должным образом.  
  
## <a name="next-steps"></a>Следующие шаги  
 В этом пошаговом руководстве описываются основные принципы привязки именованного диапазона к полю в базе данных. Ниже приводятся некоторые из возможных последующих задач.  
  
-   Кэширование данных использовать в автономном режиме. Дополнительные сведения см. в разделе [как: кэширование данных для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Привязка ячеек к нескольким столбцам в таблице, вместо к одному полю. Дополнительные сведения см. в разделе [Пошаговое руководство: сложная привязка данных в проекте уровня документа](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Используйте <xref:System.Windows.Forms.BindingNavigator> для прокрутки записей. Дополнительные сведения см. в разделе [как: перемещения данных с помощью элемента управления BindingNavigator в Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Данные в решениях Office](../vsto/data-in-office-solutions.md)   
 [Пошаговое руководство. Сложная привязка данных в проекте уровня документа](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  