---
title: "Как: программное создание документов | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
ms.assetid: c24bb8a3-1303-438e-9b33-ba8b00b29c3b
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b1935b7657e7aad612b855ecd4e9c1c8e222c952
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-new-documents"></a>Практическое руководство. Программное создание документов
  При создании документа программным образом новый документ является собственным объектом <xref:Microsoft.Office.Interop.Word.Document>. Этот объект не имеет дополнительных событий и возможностей привязки данных, которые имеет ведущий элемент <xref:Microsoft.Office.Tools.Word.Document>. Для получения дополнительной информации см. [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 При разработке проекта на уровне документа добавлять ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> в проект программным образом нельзя. В проекте надстройки VSTO любой объект <xref:Microsoft.Office.Interop.Word.Document> можно преобразовать в ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> во время выполнения. Дополнительные сведения см. в разделе [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-create-a-new-document-based-on-the-normal-template"></a>Создание нового документа на основе шаблона «Обычный»  
  
-   Для создания нового документа на основе шаблона «Обычный» используйте метод <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> коллекции <xref:Microsoft.Office.Interop.Word.Documents>. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]  
  
## <a name="using-custom-templates"></a>Использование пользовательских шаблонов  
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Метод имеет необязательный *шаблона* аргумент для создания нового документа на основе шаблона, отличного от обычного шаблона. Необходимо указать имя файла и полный путь к шаблону.  
  
#### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Создание нового документа на основе пользовательского шаблона  
  
-   Вызовите метод <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> коллекции <xref:Microsoft.Office.Interop.Word.Documents> и укажите путь к шаблону. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]  
  
## <a name="see-also"></a>См. также  
 [Как: Открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  