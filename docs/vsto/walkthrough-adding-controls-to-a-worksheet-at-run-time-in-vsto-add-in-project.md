---
title: "Пошаговое руководство. Добавление элементов управления на лист во время выполнения в проекте надстройки VSTO | Microsoft Docs"
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
  - "надстройки [разработка решений Office в Visual Studio], добавление элементов управления"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], добавление элементов управления"
  - "элементы управления [разработка решений Office в Visual Studio], добавление листов во время выполнения"
  - "листы, добавление элементов управления во время выполнения"
ms.assetid: 4f68677a-4789-4564-b229-02e2d4031a5f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Пошаговое руководство. Добавление элементов управления на лист во время выполнения в проекте надстройки VSTO
  Вы можете добавить элементы управления на любой открытый лист с помощью надстройки VSTO для Excel.  В этом пошаговом руководстве показано, как с помощью ленты предоставить пользователям возможность добавлять <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> и <xref:Microsoft.Office.Tools.Excel.ListObject> на лист.  Дополнительные сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для Excel.  Дополнительные сведения см. в разделе [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   предоставление пользовательского интерфейса для добавления элементов управления на лист;  
  
-   добавление элементов управления на лист;  
  
-   удаление элементов управления с листа.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## Создание проекта надстройки VSTO для Excel  
 Для начала создайте проект надстройки VSTO для Excel.  
  
#### Создание проекта надстройки VSTO для Excel  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создайте проект надстройки VSTO для Excel с именем ExcelDynamicControls.  Дополнительные сведения см. в статье [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Добавьте ссылку на сборку **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll**.  Эта ссылка потребуется для программного добавления элемента управления Windows Forms на лист далее в этом пошаговом руководстве.  
  
## Предоставление пользовательского интерфейса для добавления элементов управления на лист  
 Добавьте настраиваемую вкладку на ленту Excel.  Пользователи могут установить флажки на вкладке, чтобы добавить элементы управления на лист.  
  
#### Предоставление пользовательского интерфейса для добавления элементов управления на лист  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
2.  В диалоговом окне **Добавление нового элемента** выберите элемент **Лента \(визуальный конструктор\)**, а затем нажмите кнопку **Добавить**.  
  
     В конструкторе лент откроется файл **Ribbon1.cs** или **Ribbon1.vb** и появятся вкладка и группа по умолчанию.  
  
3.  Перетащите элемент управления CheckBox с вкладки **Элементы управления ленты Office** в **панели элементов** в группу **group1**.  
  
4.  Щелкните **CheckBox1**, чтобы выбрать его.  
  
5.  В окне **Свойства** измените следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|Кнопка|  
    |**Метка**|Кнопка|  
  
6.  Добавьте второй флажок в **group1**, а затем измените следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|NamedRange|  
    |**Метка**|NamedRange|  
  
7.  Добавьте третий флажок в **group1**, а затем измените следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|ListObject|  
    |**Метка**|ListObject|  
  
## Добавление элементов управления на лист  
 Управляемые элементы управления можно добавить только в ведущие элементы, которые служат контейнерами.  Поскольку проекты надстроек VSTO работают с любой открытой книгой, надстройка VSTO преобразует лист в ведущий элемент или получает существующий ведущий элемент перед добавлением элемента управления.  Добавьте код в обработчик событий нажатием каждого элемента управления, чтобы создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet>, основанный на открытом листе.  Затем добавьте <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> и <xref:Microsoft.Office.Tools.Excel.ListObject> в выделенный фрагмент на листе.  
  
#### Добавление элементов управления на лист  
  
1.  В конструкторе лент дважды щелкните **Кнопка**.  
  
     Обработчик событий <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> флажка **Кнопка** откроется в редакторе кода.  
  
2.  Замените обработчик событий `Button_Click` следующим кодом.  
  
     Этот код использует метод `GetVstoObject` для получения ведущего элемента, представляющего первый лист в книге, а затем добавляет элемент управления <xref:Microsoft.Office.Tools.Excel.Controls.Button> в выбранную ячейку.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#2)]  
  
3.  В **обозревателе решений** выберите файл Ribbon1.cs или Ribbon1.vb.  
  
4.  В меню **Вид** выберите пункт **Конструктор**.  
  
5.  В конструкторе лент дважды щелкните **NamedRange**.  
  
6.  Замените обработчик событий `NamedRange_Click` следующим кодом.  
  
     Этот код использует метод `GetVstoObject` для получения ведущего элемента, представляющего первый лист в книге, а затем определяет элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> для выбранных ячеек.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#3)]  
  
7.  В конструкторе лент дважды щелкните **ListObject**.  
  
8.  Замените обработчик событий `ListObject_Click` следующим кодом.  
  
     Этот код использует метод `GetVstoObject` для получения ведущего элемента, представляющего первый лист в книге, а затем определяет элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> для выбранных ячеек.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#4)]  
  
9. Добавьте следующие операторы в начало файла кода ленты.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#1)]  
  
## Удаление элементов управления с листа  
 Элементы управления не сохраняются при сохранении и закрытии листа.  Все созданные элементы управления Windows Forms следует удалить программными средствами до сохранения листа, при этом только контур элемента управления появится при повторном открытии книги.  Добавьте код в событие <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>, которое удаляет элементы управления Windows Forms из коллекции элементов управления созданного ведущего элемента управления.  Дополнительные сведения см. в разделе [Сохранение динамических элементов управления в документах Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### Удаление элементов управления с листа  
  
1.  В **обозревателе решений** выберите файл ThisAddIn.cs или ThisAddIn.vb.  
  
2.  В меню **Представление** выберите пункт **Код**.  
  
3.  Добавьте следующий метод в класс ThisAddIn.  Этот код получает первый лист в книге, а затем использует метод `HasVstoObject`, чтобы проверить, содержит ли лист созданный объект листа.  Если созданный объект листа содержит элементы управления, код получает его и проходит по коллекции элементов управления, удаляя элементы управления.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#6)]  
  
4.  В C\# необходимо создать обработчик для события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>.  Этот код можно поместить в методе `ThisAddIn_Startup`.  Дополнительные сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  Замените метод `ThisAddIn_Startup` следующим кодом.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#5)]  
  
## Тестирование решения  
 Добавьте элементы управления на лист, выбрав их в настраиваемой вкладке на ленте.  При сохранении листа эти элементы управления будут удалены.  
  
#### Тестирование решения  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Выберите любую ячейку на листе Sheet1.  
  
3.  Перейдите на вкладку **Надстройки**.  
  
4.  В группе **group1** щелкните **Кнопка**.  
  
     В выбранной ячейке появится кнопка.  
  
5.  Выберите другую ячейку на листе Sheet1.  
  
6.  В группе **group1** щелкните **NamedRange**.  
  
     Именованный диапазон будет определен для выбранной ячейки.  
  
7.  Выберите ряд ячеек на листе Sheet1.  
  
8.  В группе **group1** щелкните **ListObject**.  
  
     Объект списка будет добавлен для выделенных ячеек.  
  
9. Сохраните лист.  
  
     Элементы управления, добавленные в Sheet1, больше не отображаются.  
  
## Следующие действия  
 Дополнительные сведения об элементах управления в проектах надстройки VSTO для Excel см. в следующем разделе:  
  
-   Сведения о сохранении элементов управления на листе см. в примере надстройки VSTO для Excel в разделе [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## См. также  
 [Решения Excel](../vsto/excel-solutions.md)   
 [Общие сведения об использовании элементов управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)  
  
  