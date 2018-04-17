---
title: 'Как: программное извлечение символов начала и завершения в диапазонах | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a79112e80885dfd64b85a90125ea059277725d33
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Практическое руководство. Программное извлечение символов начала и завершения в диапазонах
  В этом примере показано, как получить позиции символов начала и конца диапазона.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Получение начального и конечного знаков диапазона в настройке уровня документа  
  
1.  Получите значения свойств <xref:Microsoft.Office.Interop.Word.Range.Start%2A> и <xref:Microsoft.Office.Interop.Word.Range.End%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> . В следующем примере кода возвращается позиция начала и конца второго предложения в документе. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-an-vsto-add-in"></a>Получение начального и конечного знаков диапазона с помощью надстройки VSTO  
  
1.  Получите значения свойств <xref:Microsoft.Office.Interop.Word.Range.Start%2A> и <xref:Microsoft.Office.Interop.Word.Range.End%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> . В следующем примере кода возвращается позиция начала и конца второго предложения в активном документе. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Как: программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Как: программным образом сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Как: программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Как: программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Практическое руководство. Программный подсчет символов в документах](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  