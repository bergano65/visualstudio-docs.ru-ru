---
title: Программные ограничения ведущих элементов и элементов управления ведущего приложения | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: c47b1158eefda91e83ce85a5a7403f3f8f0249a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Программные ограничения ведущих элементов и элементов управления ведущего приложения
  Каждый ведущий элемент и элемент управления ведущего приложения создается, чтобы работать аналогично собственному объекту Microsoft Office Word или Microsoft Office Excel с дополнительными функциями. Но есть ряд фундаментальных различий между поведением во время выполнения ведущих элементов и элементов управления ведущего приложения с одной стороны и собственных объектов Office с другой стороны.  
  
 Общие сведения о ведущих элементах и элементах управления ведущего приложения см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-creating-host-items"></a>Программное создание ведущих элементов  
 При программном создании или открытии документа, книги или листа во время выполнения с использованием объектной модели Word или Excel элемент не является ведущим. Вместо этого новый объект является собственным объектом Office. Например, при использовании метода <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> для создания документа Word во время выполнения он будет собственным объектом <xref:Microsoft.Office.Interop.Word.Document> , а не ведущим элементом <xref:Microsoft.Office.Tools.Word.Document> . Аналогично, при создании листа с помощью метода <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> во время выполнения вы получаете собственный объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , а не ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> .  
  
 В проектах уровня документа нельзя создавать ведущие элементы во время выполнения. Ведущие элементы можно создавать в проектах уровня документа только во время разработки. Дополнительные сведения см. в разделах [Document Host Item](../vsto/document-host-item.md), [Workbook Host Item](../vsto/workbook-host-item.md)и [Worksheet Host Item](../vsto/worksheet-host-item.md).  
  
 В проектах надстроек VSTO можно создавать ведущие элементы <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>и <xref:Microsoft.Office.Tools.Excel.Worksheet> во время выполнения. Для получения дополнительной информации см. [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="programmatically-creating-host-controls"></a>Программное создание элементов управления ведущего приложения  
 Во время выполнения можно программными средствами добавлять элементы управления ведущего приложения в ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> или <xref:Microsoft.Office.Tools.Excel.Worksheet> . Для получения дополнительной информации см. [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Нельзя добавлять элементы управления ведущего приложения в собственный объект <xref:Microsoft.Office.Interop.Word.Document> или <xref:Microsoft.Office.Interop.Excel.Worksheet>.  
  
> [!NOTE]  
>  Следующие элементы управления ведущего приложения нельзя добавлять программными средствами в листы и документы: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>и <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## <a name="understanding-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Основные сведения о различиях между ведущими элементами, элементами управления ведущего приложения и собственными объектами Office  
 Для каждого ведущего элемента и элемента управления ведущего приложения существует собственный объект Microsoft Office Word или Microsoft Office Excel. С помощью свойства InnerObject ведущего элемента или элемента управления ведущего приложения доступны базового объекта. Однако невозможно привести собственный объект Office к соответствующему ведущему элементу или элементу управления ведущего приложения. При попытке привести собственный объект Office к типу ведущего элемента или элемента управления ведущего приложения возникает исключение <xref:System.InvalidCastException> .  
  
 Существует несколько сценариев, в которых различия между типами ведущих элементов, элементов управления ведущего приложения и базовых собственных объектов Office могут повлиять на код.  
  
### <a name="passing-host-controls-to-methods-and-properties"></a>Передача элементов управления ведущего приложения в методы и свойства  
 В приложении Word невозможно передать элемент управления ведущего приложения в метод или свойство, для которого требуется собственный объект Word в качестве параметра. Чтобы вернуть базовый собственный объект Word, необходимо использовать свойство InnerObject элемента управления ведущего приложения. Например, можно передать объект <xref:Microsoft.Office.Interop.Word.Bookmark> в метод путем передачи в метод свойства <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
 В Excel необходимо использовать свойство InnerObject элемента управления ведущего приложения для передачи элемента управления ведущего приложения в метод или свойство, если метод или свойство ожидают базовый объект Excel.  
  
 В приведенном ниже примере создается элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> , который затем передается в метод <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> . Код использует свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> именованного диапазона для возврата базового объекта <xref:Microsoft.Office.Interop.Excel.Range> Office, требующегося для метода <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> .  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>Возвращаемые типы собственных методов и свойств Office  
 Большинство методов и свойств ведущих элементов возвращают собственные объекты Office, на которых основаны ведущие элементы. Например, свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.NamedRange> в Excel возвращает объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , а не ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> . Аналогично, свойство <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в Word возвращает объект <xref:Microsoft.Office.Interop.Word.Document> , а не ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> .  
  
### <a name="accessing-collections-of-host-controls"></a>Доступ к коллекциям элементов управления ведущего приложения  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] не предоставляет отдельных коллекций для каждого типа элементов управления ведущего приложения. Вместо этого используйте свойство элементов управления ведущего элемента для перебора всех управляемых элементов управления (элементы управления ведущего приложения и элементы управления Windows Forms) в документе или листе и найдите элементы, соответствующие типу элемента управления ведущего приложения, которые вас интересуют. В примере кода ниже рассматривается каждый элемент управления в документе Word и определяется, является ли он <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 Дополнительные сведения о свойствах элементов управления ведущих элементов см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Объектные модели Word и Excel включают свойства, которые предоставляют коллекции собственных элементов управления для документов и листов. С помощью этих свойств нельзя получить доступ к управляемым элементам управления. Например, невозможно перечислить каждый элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> в документе с помощью свойства <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> объекта <xref:Microsoft.Office.Interop.Word.Document> или свойства <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> объекта <xref:Microsoft.Office.Tools.Word.Document>. Эти свойства включают в документ только элементы управления <xref:Microsoft.Office.Interop.Word.Bookmark> ; они не включают в документ элементы управления ведущего приложения <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Ведущие элементы листа](../vsto/worksheet-host-item.md)   
 [Ведущий элемент книги](../vsto/workbook-host-item.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)  
  
  