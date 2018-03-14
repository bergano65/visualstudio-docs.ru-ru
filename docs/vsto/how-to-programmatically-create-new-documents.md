---
title: "Как: программное создание документов | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 09e6f9e0e2bc6a001f6a2b67c733f11bfb725563
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-create-new-documents"></a>Практическое руководство. Программное создание документов
  При создании документа программным образом новый документ является собственным объектом <xref:Microsoft.Office.Interop.Word.Document>. Этот объект не имеет дополнительных событий и возможностей привязки данных, которые имеет ведущий элемент <xref:Microsoft.Office.Tools.Word.Document>. Для получения дополнительной информации см. [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 При разработке проекта на уровне документа добавлять ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> в проект программным образом нельзя. В проекте надстройки VSTO любой объект <xref:Microsoft.Office.Interop.Word.Document> можно преобразовать в ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> во время выполнения. Для получения дополнительной информации см. [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
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
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  