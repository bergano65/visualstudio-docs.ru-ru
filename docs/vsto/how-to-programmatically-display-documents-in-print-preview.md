---
title: Руководство. программное отображение документов в режиме предварительного просмотра
description: Сведения о программном отображении документов в режиме предварительного просмотра в документе Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14005f465fd4394e86450017530de457a97b3d4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885551"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Руководство. программное отображение документов в режиме предварительного просмотра
  Если решение создает отчет, может потребоваться отображение отчета пользователю в режиме предварительного просмотра отчета.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="procedures-for-document-level-customizations"></a>Процедуры для настроек на уровне документа

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Отображение документа в режиме предварительного просмотра путем вызова метода PrintPreview

1. Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> класса <xref:Microsoft.Office.Tools.Word.Document> . Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Отображение документа в режиме предварительного просмотра путем установки свойства PrintPreview

1. Присвойте свойству <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> объекта <xref:Microsoft.Office.Interop.Word.Application> значение **true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="procedures-for-vsto-add-ins"></a>Процедуры для надстроек VSTO

### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Отображение документа в режиме предварительного просмотра путем вызова метода PrintPreview

1. Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> документа <xref:Microsoft.Office.Interop.Word.Document> , который требуется открыть в режиме предварительного просмотра. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]

### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Отображение документа в режиме предварительного просмотра путем установки свойства PrintPreview

1. Присвойте свойству <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> объекта <xref:Microsoft.Office.Interop.Word.Application> значение **true**.

     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]

## <a name="see-also"></a>См. также раздел
- [Руководство. Программная печать документов](../vsto/how-to-programmatically-print-documents.md)
- [Руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)
- [Руководство. Программное создание новых документов](../vsto/how-to-programmatically-create-new-documents.md)
