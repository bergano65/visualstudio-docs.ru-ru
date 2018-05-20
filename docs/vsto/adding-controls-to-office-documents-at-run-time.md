---
title: Добавление элементов управления в документы Office во время выполнения
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af280d407a8453b66658ee5395a88d2b91b991b7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Добавление элементов управления в документы Office во время выполнения
  Можно добавить элементы управления в документ Microsoft Office Word и книги Microsoft Office Excel во время выполнения. Также можно удалить их во время выполнения. Элементы управления, которые можно добавить или удалить во время выполнения, называются *динамических элементов управления*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 Этот раздел содержит сведения по следующим темам.  

-   [Управление элементами управления во время выполнения с помощью коллекций элементов управления](#ControlsCollection).  

-   [Добавление элементов управления ведущего приложения в документы](#HostControls).  

-   [Добавление элементов управления Windows Forms в документы](#WindowsForms).  

 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как I: добавить элементы управления в документ контактной во время выполнения?](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Управление элементами управления во время выполнения с помощью коллекций элементов управления  
 Чтобы добавить, получить или удалить элементы управления во время выполнения, используйте вспомогательные методы объектов <xref:Microsoft.Office.Tools.Excel.ControlCollection> и <xref:Microsoft.Office.Tools.Word.ControlCollection> объектов.  

 Способ доступа к этим объектам зависит от типа разрабатываемого проекта.  

-   В проекте уровня документа для Excel используйте свойство <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> классов `Sheet1`, `Sheet2`и `Sheet3` . Дополнительные сведения об этих классах см. в разделе [ведущий элемент листа](../vsto/worksheet-host-item.md).  

-   В проекте уровня документа для Word используйте свойство <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> класса `ThisDocument` . Дополнительные сведения об этом классе см. в разделе [ведущий элемент документа](../vsto/document-host-item.md).  

-   В проекте слова надстройки VSTO для Excel или Word, используйте `Controls` свойство <xref:Microsoft.Office.Tools.Excel.Worksheet> или <xref:Microsoft.Office.Tools.Word.Document> , создаваемого во время выполнения. Дополнительные сведения о создании этих объектов во время выполнения см. в разделе [документов расширить Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="add-controls"></a>Добавление элементов управления  
 Типы <xref:Microsoft.Office.Tools.Excel.ControlCollection> И <xref:Microsoft.Office.Tools.Word.ControlCollection> включают вспомогательные методы, которые можно использовать для добавления элементов управления ведущего приложения и общих элементов управления Windows Forms в документы и листы. Каждое имя метода имеет формат `Add`*класс_элемента_управления*&gt; (где *класс_элемента_управления* — это имя класса элемента управления, который требуется добавить). Например, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в документ, используйте метод <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> .  

 В следующем примере кода показано, как добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> в `Sheet1` в проекте уровня документа для Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="access-and-delete-controls"></a>Доступ и удаление элементов управления  
 Можно использовать `Controls` свойство <xref:Microsoft.Office.Tools.Excel.Worksheet> или <xref:Microsoft.Office.Tools.Word.Document> для перебора всех элементов управления в документе, включая элементы управления, добавленные во время разработки. Элементы управления, добавляемые во время разработки, также называются *статическими элементами управления*.  

 Динамические элементы управления можно удалить путем вызова `Delete` метод элемента управления или путем вызова `Remove` метод каждой коллекции элементов управления. В следующем примере кода показано использование метода <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> для удаления <xref:Microsoft.Office.Tools.Excel.NamedRange> из `Sheet1` в проекте уровня документа для Excel.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 Не удается удалить статические элементы управления во время выполнения. При попытке использовать `Delete` или `Remove` метод, чтобы удалить статический элемент управления <xref:Microsoft.Office.Tools.CannotRemoveControlException> будет создано.  

> [!NOTE]  
>  Не удаляйте программным образом элементы управления в обработчике событий `Shutdown` документа. Когда возникает событие `Shutdown` , элементы пользовательского интерфейса документа недоступны. Если требуется удалить элементы управления перед закрытием документа, добавьте код в обработчик другого типа событий, например <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> или <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> для Word либо <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>или <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> для Excel.  

##  <a name="HostControls"></a> Добавление элементов управления ведущего приложения в документы  
 Если элементы управления ведущего приложения программно добавляются в документ, необходимо указать имя, которое однозначно определяет элемент управления, и расположение для добавления элемента управления в документе. Дополнительные инструкции см. в следующих разделах:  

-   [Как: Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

-   [Как: Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

-   [Как: Добавление элементов управления диаграммой на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)  

-   [Как: Добавление содержимого элементов управления в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)  

-   [Как: Добавление закладок в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

 Дополнительные сведения об элементах управления ведущего приложения см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).  

 Когда документ сохраняется, а затем закрывается, все динамически созданные элементы управления будут отключены от событий и потеряют функции привязки данных. Можно добавить в решение код для повторного создания элементов управления ведущего приложения при повторном открытии документа. Дополнительные сведения см. в разделе [сохранение динамических элементов управления в документы Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Вспомогательные методы для элементов управления ведущего приложения не предоставляются, так как следующие элементы управления не могут быть программно добавлены в документы: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>и <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Добавление элементов управления Windows Forms в документы  
 При программном добавлении элемента управления Windows Forms в документ необходимо указать расположение и имя, которое однозначно определяет элемент управления. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] предоставляет вспомогательные методы для каждого элемента управления. Эти методы являются перегруженными, поэтому можно передавать или диапазон, или конкретные координаты расположения элемента управления.  

 Если сохранить и закрыть документ, все динамически созданные элементы управления Windows Forms будут удалены из документа. Можно добавить в решение код для повторного создания элементов управления при повторном открытии документа. Если создавать элементы управления Windows Forms с помощью надстройки VSTO, оболочки ActiveX для элементов управления остаются в документе. Дополнительные сведения см. в разделе [сохранение динамических элементов управления в документы Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  В защищенные документы нельзя программно добавить элементы управления Windows Forms. Если программно снять защиту документа Word или листа Excel, чтобы добавить элемент управления, необходимо написать дополнительный код для удаления оболочки ActiveX элемента управления при закрытии документа. Оболочки ActiveX элементов управления не удаляются из защищенных документов автоматически.  

### <a name="add-custom-controls"></a>Добавление пользовательских элементов управления  
 Если вы хотите добавить <xref:System.Windows.Forms.Control> , который не поддерживается доступными вспомогательными методами, например пользовательский элемент управления, выполните следующие действия.  

-   В Excel следует использовать один из методов <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> объекта <xref:Microsoft.Office.Tools.Excel.ControlCollection> .  

-   В Word следует использовать один из методов <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> объекта <xref:Microsoft.Office.Tools.Word.ControlCollection> .  

 Чтобы добавить элемент управления, передайте <xref:System.Windows.Forms.Control>, расположение элемента управления и имя, которое однозначно определяет элемент управления `AddControl` метод. `AddControl` Метод возвращает объект, определяющий, как элемент управления взаимодействует с листом или документом. `AddControl` Возвращает <xref:Microsoft.Office.Tools.Excel.ControlSite> (для Excel) или <xref:Microsoft.Office.Tools.Word.ControlSite> (для Word).  

 В следующем примере кода показано использование метода <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> для динамического добавления пользовательского элемента управления в лист в проекте уровня документа для Excel. В этом примере пользовательский элемент управления называется `UserControl1`, а <xref:Microsoft.Office.Interop.Excel.Range> называется `range1`. Чтобы использовать этот пример, запустите его из `Sheet` *n* класса в проекте.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="use-members-of-custom-controls"></a>Использование членов пользовательских элементов управления  
 После этого `AddControl` методы для добавления элемента управления в лист или документ есть два разных объекта элемента управления:  

-   <xref:System.Windows.Forms.Control> , представляющий пользовательский элемент управления.  

-   `ControlSite`, `OLEObject`, Или `OLEControl` объект, представляющий элемент управления после его добавления в лист или документ.  

 Многие свойства и методы этих элементов управления являются общими. Очень важно обращаться к этим членам через надлежащий элемент управления.  

-   Для доступа к членам, относящимся только к пользовательскому элементу управления, используйте <xref:System.Windows.Forms.Control>.  

-   Для доступа к членам, которые являются общими для элементов управления, используйте `ControlSite`, `OLEObject`, или `OLEControl` объекта.  

 При доступе к общему члену из <xref:System.Windows.Forms.Control>может возникнуть сбой без предупреждения или уведомления либо может быть получен недопустимый результат. Всегда использовать методы и свойства `ControlSite`, `OLEObject`, или `OLEControl` объект, если метод или свойство не поддерживается; затем должны выполняется ссылка <xref:System.Windows.Forms.Control>.  

 Например, оба <xref:Microsoft.Office.Tools.Excel.ControlSite> класса и <xref:System.Windows.Forms.Control> класс имеет `Top` свойства. Чтобы получить или задать расстояние между верхней границей элемента управления и верхней частью документа, используйте свойство <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> объекта <xref:Microsoft.Office.Tools.Excel.ControlSite>, а не свойство <xref:System.Windows.Forms.Control.Top%2A> объекта <xref:System.Windows.Forms.Control>.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>См. также  
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Сохранение динамических элементов управления в документы Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Как: Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Как: Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Как: Добавление элементов управления диаграммой на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Как: Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Как: Добавление закладок в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Элементы управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Как: Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
