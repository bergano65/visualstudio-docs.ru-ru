---
title: Пошаговое руководство. Простая привязка данных в проекте уровня документа
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3b573842aee5f00f161213cf3e01dfcc4c8ba93
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066653"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Пошаговое руководство. Простая привязка данных в проекте уровня документа
  В этом пошаговом руководстве демонстрируются основные принципы привязки данных в проекте уровня документа. Одного поля данных в базе данных SQL Server привязан к именованному диапазону в Microsoft Office Excel. Также показаны способы добавления элементов управления, которые позволяют прокручивать все записи в таблице.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В данном пошаговом руководстве рассмотрены следующие задачи:

- Создание источника данных для проекта Excel.

- Добавление элементов управления на лист.

- Прокрутки записей базы данных.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Доступ к серверу с образцом базы данных "Борей" SQL Server.

- Разрешения на чтение и запись к базе данных SQL Server.

## <a name="create-a-new-project"></a>Создание нового проекта
 На этом шаге вы создадите проект книги Excel.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект книги Excel с именем **простая привязка данных**, с помощью Visual Basic или C#. Убедитесь, что **создания документа** выбран. Дополнительные сведения см. в разделе [Как Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio открывает новую книгу Excel в конструкторе и добавляет **простая привязка данных** проект **обозревателе решений**.

## <a name="create-the-data-source"></a>Создание источника данных
 С помощью окна **Источники данных** добавьте типизированный набор данных в свой проект.

### <a name="to-create-the-data-source"></a>Создание источника данных

1. Если **источников данных** окно не отображается, откройте его в строке меню выберите **представление** > **Other Windows**  >   **Источники данных**.

2. Выберите команду **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

3. Выберите **базы данных** и нажмите кнопку **Далее**.

4. Выберите подключение данных к базе данных SQL Server Northwind или добавьте новое подключение с использованием **новое подключение** кнопки.

5. После выбора или создания подключения нажмите кнопку **Далее**.

6. Очистить параметр, чтобы сохранить подключение, если он выбран, а затем нажмите кнопку **Далее**.

7. Разверните **таблиц** узел в **объектов базы данных** окна.

8. Установите флажок рядом с полем **клиентов** таблицы.

9. Нажмите кнопку **Готово**.

   Мастер добавляет **клиентов** таблицы **источников данных** окна. Он также добавляет типизированный набор данных в проект, который является видимым в **обозревателе решений**.

## <a name="add-controls-to-the-worksheet"></a>Добавление элементов управления на лист
 В этом пошаговом руководстве требуется два именованных диапазонов и четыре кнопки на первом листе. Во-первых, добавьте два именованных диапазонов из **источников данных** окна таким образом, чтобы они автоматически привязываются к источнику данных. Добавьте кнопки, из **элементов**.

### <a name="to-add-two-named-ranges"></a>Чтобы добавить два именованных диапазонов

1. Убедитесь, что *Мой простой Binding.xlsx данных* книга открыта в конструкторе Visual Studio с **Sheet1** отображается.

2. Откройте **источников данных** окне и разверните **клиентов** узла.

3. Выберите **CompanyName** столбец, а затем щелкните стрелку раскрывающегося списка, который отображается.

4. Выберите **NamedRange** в раскрывающемся списке, а затем перетащите **CompanyName** столбца в ячейку **A1**.

     Объект <xref:Microsoft.Office.Tools.Excel.NamedRange> управления с именем `companyNameNamedRange` создается в ячейке **A1**. В то же время <xref:System.Windows.Forms.BindingSource> с именем `customersBindingSource`, адаптер таблицы и <xref:System.Data.DataSet> экземпляр добавляются в проект. Элемент управления привязан к <xref:System.Windows.Forms.BindingSource>, который, в свою очередь, привязан к <xref:System.Data.DataSet> экземпляра.

5. Выберите **CustomerID** столбца в **источников данных** окно и щелкните стрелку раскрывающегося списка, который отображается.

6. Нажмите кнопку **NamedRange** в раскрывающемся списке, а затем перетащите **CustomerID** столбца в ячейку **B1**.

7. Другой <xref:Microsoft.Office.Tools.Excel.NamedRange> управления с именем `customerIDNamedRange` создается в ячейке **B1**и привязывается к <xref:System.Windows.Forms.BindingSource>.

### <a name="to-add-four-buttons"></a>Чтобы добавить четыре кнопки

1. Из **стандартные элементы управления** вкладке **элементов**, добавьте <xref:System.Windows.Forms.Button> управления ячейку **A3** листа.

    Эта кнопка называется `Button1`.

2. Добавьте еще три кнопки в следующие ячейки в указанном порядке, таким образом, имена как показано:

   |ячейки|(Имя)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   Следующий шаг — добавить текст для кнопок и в C# добавьте обработчики событий.

## <a name="initialize-the-controls"></a>Инициализация элементов управления
 Задать текст кнопки и добавьте обработчики событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> событий.

### <a name="to-initialize-the-controls"></a>Инициализация элементов управления

1. В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1.vb** или **Sheet1.cs**, а затем нажмите кнопку **просмотреть код** в контекстном меню.

2. Добавьте следующий код, чтобы `Sheet1_Startup` метод для задания текста для каждой кнопки.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. Только в C# добавьте обработчики событий для кнопки события щелчка `Sheet1_Startup` метод.

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   Теперь добавьте код для обработки <xref:System.Windows.Forms.Control.Click> этих кнопок, чтобы пользователь может просматривать по записям.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Добавьте код, чтобы включить прокрутку записей
 Добавьте код для <xref:System.Windows.Forms.Control.Click> обработчик событий для каждой кнопки для перемещения по записям.

### <a name="to-move-to-the-first-record"></a>Чтобы перейти к первой записи

1. Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button1` и добавьте следующий код, чтобы перейти к первой записи:

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>Для перемещения к предыдущей записи

1. Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button2` и добавьте следующий код, чтобы изменить положение обратно на единицу:

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>Для перемещения к следующей записи

1. Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button3` и добавьте следующий код, чтобы переместить позицию на единицу:

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>Чтобы перейти к последней записи

1. Добавьте обработчик событий для <xref:System.Windows.Forms.Control.Click> событие `Button4` и добавьте следующий код, чтобы перейти к последней записи:

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать книгу, чтобы убедиться в том, что можно выполнять поиск записей в базе данных.

### <a name="to-test-your-workbook"></a>Проверка книги

1. Нажмите клавишу **F5** для запуска проекта.

2. Убедитесь, что первая запись отображается в ячейках **A1** и **B1**.

3. Нажмите кнопку **>** (`Button3`) кнопку и убедитесь, что следующая запись отображается в ячейке **A1** и **B1**.

4. Щелкните другие кнопки прокрутки, чтобы убедиться, что запись изменяется должным образом.

## <a name="next-steps"></a>Следующие шаги
 В этом пошаговом руководстве описываются основные принципы привязки именованного диапазона к полю в базе данных. Ниже приводятся некоторые из возможных последующих задач.

- Кэширование данных использования в автономном режиме. Дополнительные сведения см. в разделе [Как Кэшировать данные для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Привязка ячеек к нескольким столбцам в таблице, а не с одним полем. Дополнительные сведения см. в разделе [Пошаговое руководство: Сложная привязка данных в проекте уровня документа](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).

- Используйте <xref:System.Windows.Forms.BindingNavigator> для прокрутки записей. Дополнительные сведения см. в разделе [Как Навигация по набору данных с элементом управления Windows Forms BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>См. также
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Данные в решениях Office](../vsto/data-in-office-solutions.md)
- [Пошаговое руководство: Сложная привязка данных в проекте уровня документа](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
