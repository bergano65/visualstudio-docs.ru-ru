---
title: 'Практическое: программное Извлечение знаков начала и завершения в диапазонах'
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
ms.openlocfilehash: 1244fb2ba0a9e902d4dd853e7bef25376a205a0e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674358"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Практическое: программное Извлечение знаков начала и завершения в диапазонах
  В этом примере показано, как получить позиции символов начала и конца диапазона.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Получение начального и конечного знаков диапазона в настройке уровня документа  
  
1.  Получите значения свойств <xref:Microsoft.Office.Interop.Word.Range.Start%2A> и <xref:Microsoft.Office.Interop.Word.Range.End%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> . В следующем примере кода возвращается позиция начала и конца второго предложения в документе. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Получение начального и конечного знаков диапазона с помощью надстройки VSTO  
  
1.  Получите значения свойств <xref:Microsoft.Office.Interop.Word.Range.Start%2A> и <xref:Microsoft.Office.Interop.Word.Range.End%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> . В следующем примере кода возвращается позиция начала и конца второго предложения в активном документе. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>См. также  
 [Практическое: программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое: программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Практическое: программно сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Практическое: программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Практическое: программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Практическое: программно подсчет символов в документах](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  