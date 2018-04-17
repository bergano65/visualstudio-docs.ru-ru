---
title: 'Как: программное отображение документов в режиме предварительного просмотра | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bca26eb30ed9c468d154dbba6e2f126d3c61050f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Практическое руководство. Программное отображение документов в режиме предварительного просмотра
  Если решение создает отчет, может потребоваться отображение отчета пользователю в режиме предварительного просмотра отчета.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Процедуры для настроек уровня документа  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Отображение документа в режиме предварительного просмотра путем вызова метода PrintPreview  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> класса <xref:Microsoft.Office.Tools.Word.Document> . Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Отображение документа в режиме предварительного просмотра путем установки свойства PrintPreview  
  
1.  Присвойте свойству <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> объекта <xref:Microsoft.Office.Interop.Word.Application> значение **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Процедуры для надстроек VSTO  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Отображение документа в режиме предварительного просмотра путем вызова метода PrintPreview  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> документа <xref:Microsoft.Office.Interop.Word.Document> , который требуется открыть в режиме предварительного просмотра. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Отображение документа в режиме предварительного просмотра путем установки свойства PrintPreview  
  
1.  Присвойте свойству <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> объекта <xref:Microsoft.Office.Interop.Word.Application> значение **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>См. также  
 [Как: программная печать документов](../vsto/how-to-programmatically-print-documents.md)   
 [Как: Открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Практическое руководство. Программное создание документов](../vsto/how-to-programmatically-create-new-documents.md)  
  
  