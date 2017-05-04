---
title: "Практическое руководство. Добавление элементов управления Windows Forms в документы Office | Microsoft Docs"
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
  - "элементы управления [разработка решений Office в Visual Studio], элементы управления Windows Forms"
  - "документы [разработка решений Office в Visual Studio], элементы управления Windows Forms"
  - "Office - документы [разработка решений Office в Visual Studio], элементы управления Windows Forms"
  - "Windows Forms - элементы управления [разработка решений Office в Visual Studio], добавление"
ms.assetid: 4d188ad2-8e17-4eb0-8422-2ff56c683e3d
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Практическое руководство. Добавление элементов управления Windows Forms в документы Office
  Вы можете добавить элементы управления Windows Forms в документы Microsoft Office Word и Microsoft Office Excel во время разработки в проектах уровня документа.  Во время выполнения можно добавить элементы управления в настройки уровня документа и надстройки VSTO.  Например, можно добавить элемент управления <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> на лист, чтобы пользователи могли выбрать из списка параметров.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 В этом разделе описываются следующие задачи:  
  
-   [добавление элементов управления во время разработки;](#designtime)  
  
-   [добавление элементов управления во время выполнения в проекте на уровне документа;](#runtimedoclevel)  
  
-   [добавление элементов управления во время выполнения в надстройки VSTO.](#runtimeaddin)  
  
 ![ссылка на видео](../vsto/media/playvideo.png "ссылка на видео") Связанный демонстрационный видеоролик можно просмотреть в статье [Как добавить элементы управления на поверхность документа во время выполнения](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Добавление элементов управления во время разработки  
 Вы можете добавить элементы управления Windows Forms в документ в проекте на уровне документа во время разработки несколькими способами.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Перетаскивание элемента управления Windows Forms в документ  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе.  Сведения о создании проектов см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  На вкладке **Общие элементы управленияпанели элементов** щелкните элемент управления, который требуется добавить, и перетащите его в документ.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **\=EMBED\("WinForms.Control.Host",""\)**  в **строке формул**.  Этот текст обязательный, его не следует удалять.  
  
#### Рисование элемента управления Windows Forms в документе  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе.  Сведения о создании проектов см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  На вкладке **Общие элементы управленияпанели элементов** щелкните элемент управления, который требуется добавить.  
  
3.  Щелкните нужное место в документе, где будет находиться верхний левый угол элемента управления, и перетащите указатель к нужному правому нижнему углу элемента управления.  
  
     Элемент управления добавляется в документ с указанным местоположением и размером.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **\=EMBED\("WinForms.Control.Host",""\)**  в **строке формул**.  Этот текст обязательный, его не следует удалять.  
  
#### Добавление элемента управления Windows Forms в документ двойным щелчком элемента управления  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе.  Сведения о создании проектов см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  На вкладке **Общие элементы управленияпанели элементов** щелкните элемент управления, который требуется добавить.  
  
3.  Щелкните место, где требуется добавить элемент управления, в документе.  
  
     Элемент управления добавляется в документ с размером по умолчанию.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **\=EMBED\("WinForms.Control.Host",""\)**  в **строке формул**.  Этот текст обязательный, его не следует удалять.  
  
#### Добавление элемента управления Windows Forms в документ двойным щелчком элемента управления  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе.  Сведения о создании проектов см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  На вкладке **Общие элементы управленияпанели элементов** дважды щелкните элемент управления, который требуется добавить.  
  
     Элемент управления добавляется в центр документа или активной области документа.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **\=EMBED\("WinForms.Control.Host",""\)**  в **строке формул**.  Этот текст обязательный, его не следует удалять.  
  
#### Добавление элемента управления Windows Forms в документ нажатием клавиши ВВОД  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе.  Сведения о создании проектов см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  На вкладке **Общие элементы управленияпанели элементов** щелкните элемент управления, который требуется добавить, и нажмите ВВОД.  
  
     Элемент управления добавляется в центр документа или активной области документа.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **\=EMBED\("WinForms.Control.Host",""\)**  в **строке формул**.  Этот текст обязательный, его не следует удалять.  
  
##  <a name="runtimedoclevel"></a> Добавление элементов управления во время выполнения в проекте на уровне документа  
 Вы можете программно добавить элементы управления Windows Forms в документ во время выполнения.  В Word используйте методы свойства <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> класса `ThisDocument`.  В Excel используйте методы свойства <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> класса `Sheet`*n*.  У каждого метода есть несколько перегрузок, которые позволяют указать расположение элемента управления разными способами.  
  
 При добавлении элемента управления Windows Forms в документ во время выполнения он не сохраняется в документе при закрытии документа.  Элемент управления можно восстановить при следующем открытии документа.  Дополнительные сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Добавление элемента управления Windows Forms во время выполнения  
  
1.  Используйте метод с именем Add\<*класс элемента управления*\> \(где *класс элемента управления* — это имя класса элемента управления Windows Forms, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
     В следующем примере кода показано, как добавить <xref:Microsoft.Office.Tools.Excel.Controls.Button> в ячейку **C5** `Sheet1` в проекте уровня документа для Excel.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#4)]  
  
##  <a name="runtimeaddin"></a> Добавление элементов управления во время выполнения в надстройки VSTO  
 Вы можете добавить элементы управления Windows Forms программным способом в любой открытый документ во время выполнения.  Сначала создайте ведущий элемент, основанный на открытом документе или листе.  Затем в Word используйте методы свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> нового ведущего элемента.  В Excel используйте методы свойства <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> нового ведущего элемента.  У каждого метода есть несколько перегрузок, которые позволяют указать расположение элемента управления разными способами.  
  
 При добавлении элемента управления Windows Forms в документ во время выполнения он не сохраняется в документе при закрытии документа.  Элемент управления можно восстановить при следующем открытии документа.  Дополнительные сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Дополнительные сведения о создании ведущих элементов в проектах надстройки VSTO см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Добавление элемента управления Windows Forms во время выполнения  
  
1.  Используйте метод с именем Add\<*класс элемента управления*\> \(где *класс элемента управления* — это имя класса элемента управления Windows Forms, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
    > [!NOTE]  
    >  В проектах надстройки VSTO, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо добавить ссылку на сборку Microsoft.Office.Tools.Excel.v4.0.Utilities.dll или Microsoft.Office.Tools.Word.v4.0.Utilities.dll для получения доступа к методам Add\<*класс элемента управления*\>.  
  
     В следующем примере кода показано, как добавить <xref:Microsoft.Office.Tools.Word.Controls.Button> в первый абзац активного документа с помощью надстройки VSTO для Word.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDynamicControls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#7)]  
  
## См. также  
 [Общие сведения об использовании элементов управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Практическое руководство. Изменение размера внутри ячеек листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  