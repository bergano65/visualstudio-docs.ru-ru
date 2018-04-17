---
title: 'Как: программная Защита документов и их частей документов | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2e25dd6af67307ebf28a63893411bb2dfaa7bf61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Практическое руководство. Программная защита документов и их частей
  Вы можете добавлять защиту в документы Microsoft Office Word, чтобы запретить пользователям вносить изменения в документ.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Вы также можете помечать определенные части документа как исключения, чтобы указанные пользователи могли изменять только эти области документа. Например, можно защитить весь документ, кроме определенной закладки. При необходимости можно добавить пароль, чтобы пользователи, не знающие пароль, не могли удалить защиту документа.  
  
> [!NOTE]  
>  В следующем примере защита паролем не используется; однако вы можете рассмотреть возможность использования пароля при добавлении защиты документов. Дополнительные сведения см. в примере системы защиты документов по адресу [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Для защиты частей документов можно также использовать элементы управления содержимым. Для получения дополнительной информации см. [Практическое руководство. Защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="protecting-a-document-that-is-part-of-a-document-level-customization"></a>Защита документа, который является частью настройки уровня документа  
  
#### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>Защита документа, который является частью настройки уровня документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> класса `ThisDocument` в проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
#### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Исключение элемента управления "Закладка" из защиты документа  
  
1.  Защитите весь документ при помощи метода <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> .  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
2.  Исключите `Bookmark1` из защиты документа.  
  
     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]  
  
### <a name="compiling-the-code"></a>Компиляция кода  
 Чтобы использовать эти примеры кода, выполняйте их из класса `ThisDocument` в своем проекте. В этих примерах кода предполагается, что элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> с именем `Bookmark1` существует в документе, в котором отображается этот код.  
  
## <a name="protecting-a-document-by-using-an-vsto-add-in"></a>Защита документа с помощью надстройки VSTO  
  
#### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>Защита документа с помощью надстройки VSTO уровня приложения  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> документа <xref:Microsoft.Office.Interop.Word.Document> , который требуется защитить.  
  
     В следующем примере кода защищается активный документ. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]  
  
## <a name="see-also"></a>См. также  
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Защита паролем в документах Office](../vsto/password-protection-on-office-documents.md)   
 [Как: код разрешено выполнение с выделенным документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Практическое руководство. Добавление закладок в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  