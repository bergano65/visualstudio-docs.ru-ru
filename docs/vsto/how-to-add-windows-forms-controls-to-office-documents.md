---
title: Как выполнить Добавление элементов управления Windows forms в документы Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 816f5b8d21578b57e93dab7349bfd877da11401c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869295"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Как выполнить Добавление элементов управления Windows Forms в документы Office
  Вы можете добавить элементы управления Windows Forms в документы Microsoft Office Word и Microsoft Office Excel во время разработки в проектах уровня документа. Во время выполнения можно добавить элементы управления в настройках уровня документа и надстроек VSTO. Например, можно добавить элемент управления <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> на лист, чтобы пользователи могли выбрать из списка параметров.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 В этом разделе описываются следующие задачи.  
  
- [Добавление элементов управления во время разработки](#designtime)  
  
- [Добавление элементов управления во время выполнения в проектах уровня документа](#runtimedoclevel)  
  
- [Добавление элементов управления во время выполнения в надстройках VSTO](#runtimeaddin)  
  
  ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Добавление элементов управления в рабочую область документа во время выполнения? ](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Добавление элементов управления во время разработки  
 Вы можете добавить элементы управления Windows Forms в документ в проекте на уровне документа во время разработки несколькими способами.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Перетаскивание элемента управления Windows Forms в документ  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  В **стандартные элементы управления** вкладке **элементов**, щелкните элемент управления, который вы хотите добавить и перетащите его в документ.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.  
  
### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Рисование элемента управления Windows Forms в документе  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  В **стандартные элементы управления** вкладке **элементов**, щелкните элемент управления, который вы хотите добавить.  
  
3.  Щелкните нужное место в документе, где будет находиться верхний левый угол элемента управления, и перетащите указатель к нужному правому нижнему углу элемента управления.  
  
     Элемент управления добавляется в документ с указанным местоположением и размером.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строка формул**. Этот текст обязательный, его не следует удалять.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Добавление элемента управления Windows Forms в документ двойным щелчком элемента управления  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  В **стандартные элементы управления** вкладке **элементов**, щелкните элемент управления, который вы хотите добавить  
  
3.  Щелкните место, где требуется добавить элемент управления, в документе.  
  
     Элемент управления добавляется в документ с размером по умолчанию.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Добавление элемента управления Windows Forms в документ двойным щелчком элемента управления  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  В **стандартные элементы управления** вкладке **элементов**, дважды щелкните элемент управления, который вы хотите добавить.  
  
     Элемент управления добавляется в центр документа или активной области документа.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Добавление элемента управления Windows Forms в документ нажатием клавиши ВВОД  
  
1.  Создайте или откройте проект книги Excel или документа Word в Visual Studio, чтобы документ был виден в конструкторе. Сведения о создании проектов см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  В **стандартные элементы управления** вкладке **элементов**, щелкните элемент управления, который вы хотите добавить и нажмите клавишу **ввод** ключ.  
  
     Элемент управления добавляется в центр документа или активной области документа.  
  
    > [!NOTE]  
    >  При выборе элемента управления в Excel вы увидите **=EMBED("WinForms.Control.Host","")** в **строке формул**. Этот текст обязательный, его не следует удалять.  
  
##  <a name="runtimedoclevel"></a> Добавление элементов управления во время выполнения в проектах уровня документа  
 Можно программно добавить элементы управления Windows Forms в документ во время выполнения. В Word используйте методы свойства <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> класса `ThisDocument`. В Excel, используйте методы <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> свойство `Sheet` *n* класса. У каждого метода есть несколько перегрузок, которые позволяют указать расположение элемента управления разными способами.  
  
 При добавлении элемента управления Windows Forms в документ во время выполнения, элемент управления не сохраняются в документе при закрытии документа. Элемент управления можно восстановить при следующем открытии документа. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Добавление элемента управления Windows Forms во время выполнения  
  
1.  Используйте метод с именем Add\<*класс элемента управления*> (где *класс элемента управления* — это имя класса элемента управления Windows Forms, который вы хотите добавить, например <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
     В следующем примере кода показано, как добавить <xref:Microsoft.Office.Tools.Excel.Controls.Button> ячейку **C5** из `Sheet1` в проекте уровня документа для Excel.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a> Добавление элементов управления во время выполнения в надстройках VSTO  
 Можно добавить элементы управления Windows Forms программным способом в любой открытый документ во время выполнения. Сначала создайте ведущий элемент, основанный на открытом документе или листе. Затем в Word используйте методы свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> нового ведущего элемента. В Excel используйте методы свойства <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> нового ведущего элемента. У каждого метода есть несколько перегрузок, которые позволяют указать расположение элемента управления разными способами.  
  
 При добавлении элемента управления Windows Forms в документ во время выполнения, элемент управления не сохраняются в документе при закрытии документа. Элемент управления можно восстановить при следующем открытии документа. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Дополнительные сведения о создании ведущих элементов в проектах надстройки VSTO, см. в разделе [документов расширения Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Добавление элемента управления Windows Forms во время выполнения  
  
1.  Используйте метод с именем Add\<*класс элемента управления*> (где *класс элемента управления* — это имя класса элемента управления Windows Forms, который вы хотите добавить, например <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
    > [!NOTE]  
    >  В надстройке VSTO проектах, предназначенных [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо добавить ссылку на *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* или *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* сборки, чтобы можно было открыть добавления\<*класс элемента управления*> методы.  
  
     В следующем примере кода показано, как добавить <xref:Microsoft.Office.Tools.Word.Controls.Button> в первый абзац активного документа с помощью надстройки VSTO для Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>См. также  
 [Элементы управления Windows Forms на общие сведения о документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Практическое руководство. Изменение размера элементов управления внутри ячеек листа Excel](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
