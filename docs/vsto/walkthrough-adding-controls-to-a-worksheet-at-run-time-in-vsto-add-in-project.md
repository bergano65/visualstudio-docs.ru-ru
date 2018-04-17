---
title: 'Пошаговое руководство: Добавление элементов управления на лист во время выполнения в VSTO надстройки проекта | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47c647e2b3af6941f7b4a4d6f28eccfac2b31e2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Пошаговое руководство. Добавление элементов управления на лист во время выполнения в проекте надстройки VSTO
  Вы можете добавить элементы управления на любой открытый лист с помощью надстройки VSTO для Excel. В этом пошаговом руководстве показано, как с помощью ленты предоставить пользователям возможность добавлять <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> и <xref:Microsoft.Office.Tools.Excel.ListObject> на лист. Сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Применяется к:** информация в этой статье относится к проектам надстроек VSTO для Excel. Дополнительные сведения см. в разделе [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   предоставление пользовательского интерфейса для добавления элементов управления на лист;  
  
-   добавление элементов управления на лист;  
  
-   удаление элементов управления с листа.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="creating-a-new-excel-vsto-add-in-project"></a>Создание проекта надстройки VSTO для Excel  
 Для начала создайте проект надстройки VSTO для Excel.  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Создание проекта надстройки VSTO для Excel  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], создайте проект надстройки VSTO для Excel с именем **ExcelDynamicControls**. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Добавьте ссылку на **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** сборки. Эта ссылка потребуется для программного добавления элемента управления Windows Forms на лист далее в этом пошаговом руководстве.  
  
## <a name="providing-a-ui-to-add-controls-to-a-worksheet"></a>Предоставление пользовательского интерфейса для добавления элементов управления на лист  
 Добавьте настраиваемую вкладку на ленту Excel. Пользователи могут установить флажки на вкладке, чтобы добавить элементы управления на лист.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Предоставление пользовательского интерфейса для добавления элементов управления на лист  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
2.  В **Добавление нового элемента** выберите **Лента (визуальный конструктор)**, а затем нажмите кнопку **добавить**.  
  
     Файл с именем **Ribbon1.cs** или **Ribbon1.vb** откроется в конструкторе лент и отображает вкладку по умолчанию и группы.  
  
3.  Из **элементы управления ленты Office** вкладке **элементов**, перетащите элемент управления CheckBox **group1**.  
  
4.  Щелкните **CheckBox1** , чтобы выбрать его.  
  
5.  В окне **Свойства** измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**Button**|  
    |**Label**|**Button**|  
  
6.  Добавьте второй флажок в **group1**, а затем измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**NamedRange**|  
    |**Label**|**NamedRange**|  
  
7.  Добавьте третий флажок в **group1**, а затем измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**Элемент управления ListObject**|  
    |**Label**|**Элемент управления ListObject**|  
  
## <a name="adding-controls-to-the-worksheet"></a>Добавление элементов управления на лист  
 Управляемые элементы управления можно добавить только в ведущие элементы, которые служат контейнерами. Поскольку проекты надстроек VSTO работают с любой открытой книгой, надстройка VSTO преобразует лист в ведущий элемент или получает существующий ведущий элемент перед добавлением элемента управления. Добавьте код в обработчик событий нажатием каждого элемента управления, чтобы создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet>, основанный на открытом листе. Затем добавьте <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> и <xref:Microsoft.Office.Tools.Excel.ListObject> в выделенный фрагмент на листе.  
  
#### <a name="to-add-controls-to-a-worksheet"></a>Добавление элементов управления на лист  
  
1.  В конструкторе лент дважды щелкните **кнопку**.  
  
     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Обработчик событий **кнопку** флажок откроется в редакторе кода.  
  
2.  Замените обработчик событий `Button_Click` следующим кодом.  
  
     Этот код использует метод `GetVstoObject` для получения ведущего элемента, представляющего первый лист в книге, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.Controls.Button> в выбранную ячейку.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  В **обозревателе решений**, выберите файл Ribbon1.cs или Ribbon1.vb.  
  
4.  На **представление** меню, нажмите кнопку **конструктор**.  
  
5.  В конструкторе лент дважды щелкните **NamedRange**.  
  
6.  Замените обработчик событий `NamedRange_Click` следующим кодом.  
  
     Этот код использует метод `GetVstoObject` для получения ведущего элемента, представляющего первый лист в книге, а затем определяет элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> для выбранных ячеек.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  В конструкторе лент дважды щелкните **ListObject**.  
  
8.  Замените обработчик событий `ListObject_Click` следующим кодом.  
  
     Этот код использует метод `GetVstoObject` для получения ведущего элемента, представляющего первый лист в книге, а затем определяет элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> для выбранных ячеек.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. Добавьте следующие операторы в начало файла кода ленты.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="removing-controls-from-the-worksheet"></a>Удаление элементов управления с листа  
 Элементы управления не сохраняются при сохранении и закрытии листа. Все созданные элементы управления Windows Forms следует удалить программными средствами до сохранения листа, при этом только контур элемента управления появится при повторном открытии книги. Добавьте код в событие <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>, которое удаляет элементы управления Windows Forms из коллекции элементов управления созданного ведущего элемента управления. Дополнительные сведения см. в разделе [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### <a name="to-remove-controls-from-the-worksheet"></a>Удаление элементов управления с листа  
  
1.  В **обозревателе решений**, выберите файл ThisAddIn.cs или ThisAddIn.vb.  
  
2.  На **представление** меню, нажмите кнопку **кода**.  
  
3.  Добавьте следующий метод в класс ThisAddIn. Этот код получает первый лист в книге, а затем использует метод `HasVstoObject`, чтобы проверить, содержит ли лист созданный объект листа. Если созданный объект листа содержит элементы управления, код получает его и проходит по коллекции элементов управления, удаляя элементы управления.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  В C# необходимо создать обработчик для события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. Этот код можно поместить в методе `ThisAddIn_Startup`. Дополнительные сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md). Замените метод `ThisAddIn_Startup` следующим кодом.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="testing-the-solution"></a>Тестирование решения  
 Добавьте элементы управления на лист, выбрав их в настраиваемой вкладке на ленте. При сохранении листа эти элементы управления будут удалены.  
  
#### <a name="to-test-the-solution"></a>Тестирование решения  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Выберите любую ячейку на листе Sheet1.  
  
3.  Перейдите на вкладку **Надстройки** .  
  
4.  В **group1** щелкните **кнопку**.  
  
     В выбранной ячейке появится кнопка.  
  
5.  Выберите другую ячейку на листе Sheet1.  
  
6.  В **group1** щелкните **NamedRange**.  
  
     Именованный диапазон будет определен для выбранной ячейки.  
  
7.  Выберите ряд ячеек на листе Sheet1.  
  
8.  В **group1** щелкните **ListObject**.  
  
     Объект списка будет добавлен для выделенных ячеек.  
  
9. Сохраните лист.  
  
     Элементы управления, добавленные в Sheet1, больше не отображаются.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения об элементах управления в проектах надстройки VSTO для Excel см. в следующем разделе:  
  
-   Дополнительные сведения о сохранении элементов управления на лист, см. VSTO для Excel надстройки пример динамических элементов управления в [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="see-also"></a>См. также  
 [Решения Excel](../vsto/excel-solutions.md)   
 [Элементы управления в документах Office Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)  
  
  