---
title: Пошаговое руководство. Обновление диаграммы на листе с помощью переключателей
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5aff631d8c9b6bd65b8ae91c5d936d2669764791
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866445"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Пошаговое руководство. Обновление диаграммы на листе с помощью переключателей
  В этом пошаговом руководстве описываются основные принципы с помощью переключателей на лист Microsoft Office Excel, чтобы дать пользователю возможность быстро переключаться между вариантами. В этом случае параметры изменение стиля диаграммы.  

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  

 Чтобы просмотреть результат в виде готового кода, см [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).  

 В данном пошаговом руководстве рассмотрены следующие задачи:  

-   Добавление группы переключателей на листе.  

-   изменение стиля диаграммы при выбранном параметре.  

> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  

## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  

## <a name="add-a-chart-to-a-worksheet"></a>Добавление диаграммы на лист  
 Можно создать проект книги Excel, который настраивает существующую книгу. В этом пошаговом руководстве будет добавление диаграммы в книгу и затем использовать эту книгу в новом решении Excel. Источником данных в этом пошаговом руководстве является листом **данные для диаграммы**.  

### <a name="to-add-the-data"></a>Для добавления данных  

1. Откройте Microsoft Excel.  

2. Щелкните правой кнопкой мыши **Sheet3** , а затем щелкните **Переименовать** в контекстном меню.  

3. Переименование листа к **данные для диаграммы**.  

4. Добавьте следующие данные для **данные для диаграммы** с ячейки A4, левый верхний угол угол и E8 правом нижнем углу.  

   ||ВОПРОС 1|ВОПРОС 2|ВОПРОС 3|ВОПРОС 4|  
   |-|--------|--------|--------|--------|  
   |Запад|500|550|550|600|  
   |Восток|600|625|675|700|  
   |Северная|450|470|490|510|  
   |Южная|800|750|775|790|  

   Добавьте диаграмму на первый лист, чтобы отобразить данные.  

### <a name="to-add-a-chart-in-excel"></a>Добавление диаграммы в Excel  

1.  На **вставить** на вкладке **диаграммы** щелкните **столбец**, а затем нажмите кнопку **все типы диаграмм**.  

2.  В **вставить диаграмму** диалоговом окне щелкните **ОК**.  

3.  На **разработки** на вкладке **данных** щелкните **Выбор данных**.  

4.  В **Выбор источника данных** диалоговое окно, щелкните в **диапазон Chartdata** и снимите все выборы по умолчанию.  

5.  В **данные для диаграммы** листа, выберите блок ячеек, содержащий числа, который включает A4 в левом верхнем углу для E8 в правом нижнем углу.  

6.  В **Выбор источника данных** диалоговом окне щелкните **ОК**.  

7.  Переместите диаграмму в правый верхний угол по ячейке **E2**.  

8.  Сохранить файл на диске C и назовите его **ExcelChart.xlsx**.  

9. Выйдите из Excel.  

## <a name="create-a-new-project"></a>Создание нового проекта  
 На этом шаге вы создадите проект книги Excel на основе **ExcelChart** книги.  

### <a name="to-create-a-new-project"></a>Создание нового проекта  

1.  Создайте проект книги Excel с именем **Моя диаграмма Excel**. В мастере выберите **Копировать существующий документ**.  

     Дополнительные сведения см. в разделе [как: проектов Office, создайте в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

2.  Нажмите кнопку **Обзор** кнопку и перейдите к книге, созданную ранее в этом пошаговом руководстве.  

3.  Нажмите кнопку **ОК**.  

     Visual Studio открывает новую книгу Excel в конструкторе и добавляет **Моя диаграмма Excel** проект **обозревателе решений**.  

## <a name="set-properties-of-the-chart"></a>Задание свойств диаграммы  
 При создании нового проекта книги Excel, который использует существующую книгу, элементы управления ведущего приложения создаются автоматически для всех именованных диапазонов, список объектов и диаграмм в книге. Можно изменить имя <xref:Microsoft.Office.Tools.Excel.Chart> элемента управления с помощью **свойства** окна.  

### <a name="to-change-the-name-of-the-chart-control"></a>Чтобы изменить имя элемента управления диаграммы  

1.  Выберите <xref:Microsoft.Office.Tools.Excel.Chart> в конструкторе и измените следующие свойства в **свойства** окна.  

    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**dataChart**|  
    |**HasLegend**|**false**|  

## <a name="add-controls"></a>Добавление элементов управления  
 На этом листе переключатели используются для предоставления пользователям возможности для быстрого изменения стиля диаграммы. Тем не менее, должны быть взаимоисключающими переключателей — при выборе одной кнопки, в то же время можно выбрать другие кнопки в группе. Это поведение не происходит по умолчанию при добавлении нескольких переключателей на лист.  

 Один из способов, чтобы добавить это поведение является группирование переключателей в пользовательский элемент управления, написание кода программной части пользовательского элемента управления и затем добавить пользовательский элемент управления на лист.  

### <a name="to-add-a-user-control"></a>Добавление пользовательского элемента управления  

1.  Выберите **Моя диаграмма Excel** в проекте **обозревателе решений**.  

2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  

3.  В **Добавление нового элемента** диалоговом окне щелкните **пользовательский элемент управления**, назовите элемент управления **ChartOptions** и нажмите кнопку **добавить**.  

### <a name="to-add-radio-buttons-to-the-user-control"></a>Добавление переключателей в пользовательский элемент управления  

1. Если пользовательский элемент управления не отображается в конструкторе, дважды щелкните **ChartOptions** в **обозревателе решений**.  

2. Из **стандартные элементы управления** вкладке **элементов**, перетащите **"переключатель"** управления в пользовательский элемент управления и измените следующие свойства.  


   | Свойство. | Значение |
   |----------|------------------|
   | **Name** | **columnChart** |
   | **Text** | **Гистограмма** |


3. Добавьте второй переключатель в пользовательский элемент управления и измените следующие свойства.  


   | Свойство. | Значение |
   |----------|---------------|
   | **Name** | **barChart** |
   | **Text** | **Линейчатая диаграмма** |


4. Добавьте третий переключатель в пользовательский элемент управления и измените следующие свойства.  


   | Свойство. | Значение |
   |----------|----------------|
   | **Name** | **lineChart** |
   | **Text** | **График** |


5. Добавьте четвертый переключатель в пользовательский элемент управления и измените следующие свойства.  

   |Свойство.|Значение|  
   |--------------|-----------|  
   |**Name**|**areaBlockChart**|  
   |**Text**|**Диаграмма с областями**|  

   Теперь напишите код, чтобы обновить диаграмму, при щелчке типа "переключатель".  

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Изменение стиля диаграммы при выборе типа "переключатель"  
 Теперь можно добавить код для изменения стиля диаграммы. Чтобы сделать это, создайте открытое событие на пользовательском элементе управления, добавьте свойство, чтобы установить тип выбора и создайте обработчик событий для `CheckedChanged` каждого переключателя.  

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Создание события и свойства по пользовательскому элементу управления  

1.  В **обозревателе решений**, щелкните правой кнопкой мыши пользовательский элемент управления и нажмите кнопку **Просмотр кода**.  

2.  Добавьте код для `ChartOptions` создаваемого класса `SelectionChanged` событий и `Selection` свойство.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Для обработки события CheckedChanged переключателей  

1.  Установите тип диаграммы в обработчике событий `CheckedChanged` переключателя `areaBlockChart`, а затем породите событие.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  

2.  Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `barChart`.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  

3.  Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `columnChart`.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  

4.  Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `lineChart`.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  

5.  В языке программирования C# для переключателей должны быть добавлены обработчики событий. Код можно добавить в конструктор `ChartOptions` под вызовом `InitializeComponent`. Сведения о том, как создавать обработчики событий, см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  

## <a name="add-the-user-control-to-the-worksheet"></a>Добавить пользовательский элемент управления на лист  
 При построении решения новый пользовательский элемент управления автоматически добавляется **элементов**. Затем можно перетащить элемент управления из **элементов** на лист.  

### <a name="to-add-the-user-control-your-worksheet"></a>Чтобы добавить пользовательский элемент управления на лист  

1.  В меню **Сборка** выберите **Собрать решение**.  

     **ChartOptions** пользовательский элемент управления добавляется к **элементов**.  

2.  В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1.vb** или **Sheet1.cs**, а затем нажмите кнопку **конструктор представлений**.  

3.  Перетащите **ChartOptions** управления из **элементов** на рабочий лист.  

     Новый элемент управления с именем `my_Excel_Chart_ChartOptions1` добавляется в проект.  

4.  Измените имя элемента управления, **ChartOptions1**.  

## <a name="change-the-chart-type"></a>Изменить тип диаграммы  
 Чтобы изменить тип диаграммы, создайте обработчик событий, который задает стиль в соответствии с параметром, выбранным в пользовательском элементе управления.  

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Чтобы изменить тип диаграммы, отображаемой на листе  

1.  Добавьте следующий обработчик событий в класс `Sheet1`.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  

2.  В C# необходимо добавить обработчик событий для пользовательского элемента управления <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> событий, как показано ниже. Сведения о том, как создавать обработчики событий, см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  

## <a name="test-the-application"></a>Тестирование приложения  
 Теперь можно протестировать книгу, чтобы убедиться, что правильно стиля диаграммы при выборе типа "переключатель".  

### <a name="to-test-your-workbook"></a>Проверка книги  

1.  Нажмите клавишу **F5** для запуска проекта.  

2.  Выберите различные переключатели.  

3.  Подтвердите, что изменения стиля диаграммы соответствуют выбору.  

## <a name="next-steps"></a>Следующие шаги  
 В этом пошаговом руководстве описываются основные принципы использования переключателей и стилей диаграмм на листах. Ниже приводятся некоторые из возможных последующих задач.  

-   Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).  

-   Использование кнопки для заполнения текстового поля. Дополнительные сведения см. в разделе [Пошаговое руководство: отображения текста в текстовом поле на листе с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  

-   Изменение форматирования листа с помощью флажков. Дополнительные сведения см. в разделе [Пошаговое руководство: изменение форматирования листа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  

## <a name="see-also"></a>См. также  
 [Пошаговые руководства с помощью Excel](../vsto/walkthroughs-using-excel.md)  

