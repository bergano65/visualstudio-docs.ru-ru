---
title: Программные ограничения ведущих элементов и элементов управления ведущего приложения
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 70e68a47d4685e3bba9e58fb225f2105f8bdabe4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966029"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Программные ограничения ведущих элементов и элементов управления ведущего приложения
  Каждый ведущий элемент и элемент управления ведущего приложения создается, чтобы работать аналогично собственному объекту Microsoft Office Word или Microsoft Office Excel с дополнительными функциями. Но есть ряд фундаментальных различий между поведением во время выполнения ведущих элементов и элементов управления ведущего приложения с одной стороны и собственных объектов Office с другой стороны.  
  
 Общие сведения о ведущих элементах и элементах управления ведущего приложения см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-create-host-items"></a>Программное создание ведущих элементов  
 При программном создании или открытии документа, книги или листа во время выполнения с использованием объектной модели Word или Excel элемент не является ведущим. Вместо этого новый объект является собственным объектом Office. Например, при использовании метода <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> для создания документа Word во время выполнения он будет собственным объектом <xref:Microsoft.Office.Interop.Word.Document> , а не ведущим элементом <xref:Microsoft.Office.Tools.Word.Document> . Аналогично, при создании листа с помощью метода <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> во время выполнения вы получаете собственный объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , а не ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> .  
  
 В проектах уровня документа нельзя создавать ведущие элементы во время выполнения. Ведущие элементы можно создавать в проектах уровня документа только во время разработки. Дополнительные сведения см. в разделе [ведущий элемент документа](../vsto/document-host-item.md), [ведущий элемент книги](../vsto/workbook-host-item.md), и [ведущий элемент листа](../vsto/worksheet-host-item.md).  
  
 В проектах надстройки VSTO, можно создать <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, или <xref:Microsoft.Office.Tools.Excel.Worksheet> ведущие элементы во время выполнения. Дополнительные сведения см. в разделе [документов расширения Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="programmatically-create-host-controls"></a>Программное создание элементов управления ведущего приложения  
 Можно программно добавить элементы управления ведущего приложения для <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet> ведущего элемента во время выполнения. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Нельзя добавлять элементы управления ведущего приложения в собственный объект <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Worksheet>.  
  
> [!NOTE]  
>  Следующие элементы управления ведущего приложения нельзя добавлять программными средствами в листы и документы: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>и <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Рассмотрим различия тип ведущие элементы, элементы управления ведущего приложения и собственных объектов Office  
 Для каждого ведущего элемента и элемента управления ведущего приложения существует собственный объект Microsoft Office Word или Microsoft Office Excel. Можно получить доступ к базовому объекту с помощью свойства InnerObject ведущего элемента или элемента управления ведущего приложения. Однако невозможно привести собственный объект Office к соответствующему ведущему элементу или элементу управления ведущего приложения. При попытке привести собственный объект Office к типу ведущего элемента или элемента управления ведущего приложения возникает исключение <xref:System.InvalidCastException> .  
  
 Существует несколько сценариев, в которых различия между типами ведущих элементов, элементов управления ведущего приложения и базовых собственных объектов Office могут повлиять на код.  
  
### <a name="pass-host-controls-to-methods-and-properties"></a>Передать элементы управления ведущего приложения к методам и свойствам  
 В приложении Word невозможно передать элемент управления ведущего приложения в метод или свойство, для которого требуется собственный объект Word в качестве параметра. Чтобы вернуть базовый собственный объект Word необходимо использовать свойство InnerObject элементов управления ведущего приложения. Например, можно передать объект <xref:Microsoft.Office.Interop.Word.Bookmark> в метод путем передачи в метод свойства <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
 В Excel необходимо использовать свойство InnerObject элементов управления ведущего приложения для передачи элемента управления ведущего приложения метод или свойство, когда метод или свойство ожидают базовый объект Excel.  
  
 В приведенном ниже примере создается элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> , который затем передается в метод <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> . Код использует свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> именованного диапазона для возврата базового объекта <xref:Microsoft.Office.Interop.Excel.Range> Office, требующегося для метода <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> .  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>Возвращаемые типы собственных методов Office и свойства  
 Большинство методов и свойств ведущих элементов возвращают собственные объекты Office, на которых основаны ведущие элементы. Например, свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.NamedRange> в Excel возвращает объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , а не ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> . Аналогично, свойство <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в Word возвращает объект <xref:Microsoft.Office.Interop.Word.Document> , а не ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> .  
  
### <a name="access-collections-of-host-controls"></a>Доступа к коллекции элементов управления ведущего приложения  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] не предоставляет отдельных коллекций для каждого типа элементов управления ведущего приложения. Вместо этого используйте свойство элементов управления ведущего элемента для перебора всех управляемых элементов управления (элементы управления ведущего приложения и элементов управления Windows Forms) в документе или листе и найдите элементы, соответствующие типу элементов управления ведущего приложения, которые вас интересуют. В примере кода ниже рассматривается каждый элемент управления в документе Word и определяется, является ли он <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 Дополнительные сведения о ведущих элементов свойства элементов управления, см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Объектные модели Word и Excel включают свойства, которые предоставляют коллекции собственных элементов управления для документов и листов. С помощью этих свойств нельзя получить доступ к управляемым элементам управления. Например, невозможно перечислить каждый элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> в документе с помощью свойства <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> объекта <xref:Microsoft.Office.Interop.Word.Document> или свойства <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> объекта <xref:Microsoft.Office.Tools.Word.Document>. Эти свойства включают в документ только элементы управления <xref:Microsoft.Office.Interop.Word.Bookmark> ; они не включают в документ элементы управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
## <a name="see-also"></a>См. также  
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Ведущий элемент листа](../vsto/worksheet-host-item.md)   
 [Ведущий элемент книги](../vsto/workbook-host-item.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)  
