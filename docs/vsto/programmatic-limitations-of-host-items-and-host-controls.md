---
title: "Программные ограничения ведущих элементов и элементов управления ведущего приложения | Microsoft Docs"
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
  - "документы Office [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "разработка приложений [разработка решений Office в Visual Studio], ведущие элементы"
  - "приложения Office [разработка решений Office в Visual Studio], ведущие элементы"
  - "ведущие элементы [разработка решений Office в Visual Studio], программные ограничения"
  - "Excel [разработка решений Office в Visual Studio], ведущие элементы"
  - "элементы управления ведущего приложения [разработка решений Office в Visual Studio], создание"
  - "настройки уровня документа [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "приложения Office [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "документы [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "элементы управления [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "элементы управления ведущего приложения [разработка решений Office в Visual Studio], передача методам и свойствам"
  - "разработка приложений [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "Excel [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "элементы управления ведущего приложения [разработка решений Office в Visual Studio], программные ограничения"
  - "документы [разработка решений Office в Visual Studio], ведущие элементы"
  - "документы Office [разработка решений Office в Visual Studio], ведущие элементы"
  - "Word [разработка решений Office в Visual Studio], ведущие элементы"
  - "настройки уровня документа [разработка решений Office в Visual Studio], ведущие элементы"
  - "Word [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
ms.assetid: 88487946-6f3d-4ea6-8de0-dd219b8002df
caps.latest.revision: 67
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Программные ограничения ведущих элементов и элементов управления ведущего приложения
  Каждый ведущий элемент и элемент управления ведущего приложения создается, чтобы работать аналогично собственному объекту Microsoft Office Word или Microsoft Office Excel с дополнительными функциями. Но есть ряд фундаментальных различий между поведением во время выполнения ведущих элементов и элементов управления ведущего приложения с одной стороны и собственных объектов Office с другой стороны.  
  
 Общие сведения о ведущих элементах и элементах управления ведущего приложения см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Программное создание ведущих элементов  
 При программном создании или открытии документа, книги или листа во время выполнения с использованием объектной модели Word или Excel элемент не является ведущим. Вместо этого новый объект является собственным объектом Office. Например, при использовании метода <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> для создания документа Word во время выполнения он будет собственным объектом <xref:Microsoft.Office.Interop.Word.Document>, а не ведущим элементом <xref:Microsoft.Office.Tools.Word.Document>. Аналогично, при создании листа с помощью метода <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> во время выполнения вы получаете собственный объект <xref:Microsoft.Office.Interop.Excel.Worksheet>, а не ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet>.  
  
 В проектах уровня документа нельзя создавать ведущие элементы во время выполнения. Ведущие элементы можно создавать в проектах уровня документа только во время разработки. Дополнительные сведения см. в разделах [Ведущий элемент документа](../vsto/document-host-item.md), [Ведущий элемент книги](../vsto/workbook-host-item.md) и [Ведущие элементы листа](../vsto/worksheet-host-item.md).  
  
 В проектах надстроек VSTO можно создавать ведущие элементы <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook> и <xref:Microsoft.Office.Tools.Excel.Worksheet> во время выполнения. Дополнительные сведения см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Программное создание элементов управления ведущего приложения  
 Во время выполнения можно программными средствами добавлять элементы управления ведущего приложения в ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet>. Для получения дополнительной информации см. [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Нельзя добавлять элементы управления ведущего приложения в собственный объект <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Worksheet>.  
  
> [!NOTE]  
>  Следующие элементы управления ведущего приложения нельзя добавлять программными средствами в листы и документы: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode> и <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## Основные сведения о различиях между ведущими элементами, элементами управления ведущего приложения и собственными объектами Office  
 Для каждого ведущего элемента и элемента управления ведущего приложения существует собственный объект Microsoft Office Word или Microsoft Office Excel. Для доступа к базовому объекту используется свойство InnerObject ведущего элемента или элемента управления ведущего приложения. Однако невозможно привести собственный объект Office к соответствующему ведущему элементу или элементу управления ведущего приложения. При попытке привести собственный объект Office к типу ведущего элемента или элемента управления ведущего приложения возникает исключение <xref:System.InvalidCastException>.  
  
 Существует несколько сценариев, в которых различия между типами ведущих элементов, элементов управления ведущего приложения и базовых собственных объектов Office могут повлиять на код.  
  
### Передача элементов управления ведущего приложения в методы и свойства  
 В приложении Word невозможно передать элемент управления ведущего приложения в метод или свойство, для которого требуется собственный объект Word в качестве параметра. Чтобы вернуть базовый собственный объект Word, необходимо использовать свойство InnerObject элемента управления ведущего приложения. Например, можно передать объект <xref:Microsoft.Office.Interop.Word.Bookmark> в метод путем передачи в метод свойства <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 В Excel необходимо использовать свойство InnerObject элемента управления ведущего приложения для передачи этого элемента в метод или свойство, если метод или свойство ожидают базовый объект Excel.  
  
 В приведенном ниже примере создается элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>, который затем передается в метод <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>. Код использует свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> именованного диапазона для возврата базового объекта <xref:Microsoft.Office.Interop.Excel.Range> Office, требующегося для метода <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>.  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#28)]  
  
### Возвращаемые типы собственных методов и свойств Office  
 Большинство методов и свойств ведущих элементов возвращают собственные объекты Office, на которых основаны ведущие элементы. Например, свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.NamedRange> в Excel возвращает объект <xref:Microsoft.Office.Interop.Excel.Worksheet>, а не ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet>. Аналогично, свойство <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в Word возвращает объект <xref:Microsoft.Office.Interop.Word.Document>, а не ведущий элемент <xref:Microsoft.Office.Tools.Word.Document>.  
  
### Доступ к коллекциям элементов управления ведущего приложения  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] не предоставляет отдельных коллекций для каждого типа элементов управления ведущего приложения. Вместо этого используйте свойство Controls ведущего элемента для перебора всех управляемых элементов управления \(как элементов управления ведущего приложения, так и элементов управления Windows Forms\) в документе или листе, а затем найдите элементы, которые соответствуют типу нужного элемента управления ведущего приложения. В примере кода ниже рассматривается каждый элемент управления в документе Word и определяется, является ли он <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#10)]  
  
 Дополнительные сведения о свойстве Controls ведущих элементов см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Объектные модели Word и Excel включают свойства, которые предоставляют коллекции собственных элементов управления для документов и листов. С помощью этих свойств нельзя получить доступ к управляемым элементам управления. Например, невозможно перечислить каждый элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> в документе с помощью свойства <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> объекта <xref:Microsoft.Office.Interop.Word.Document> или свойства <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> объекта <xref:Microsoft.Office.Tools.Word.Document>. Эти свойства включают в документ только элементы управления <xref:Microsoft.Office.Interop.Word.Bookmark>; они не включают в документ элементы управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
## См. также  
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Ведущие элементы листа](../vsto/worksheet-host-item.md)   
 [Ведущий элемент книги](../vsto/workbook-host-item.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)  
  
  