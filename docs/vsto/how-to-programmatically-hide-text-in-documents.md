---
title: Как выполнить Программное скрытие текста в документах
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ca17436e022763f606ed950cc7240d78e0ad1b68
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874917"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Как выполнить Программное скрытие текста в документах
  Текст в документе можно скрыть, установив свойство <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> объекта <xref:Microsoft.Office.Interop.Word.Range.Font%2A> для определенного фрагмента текста.  
  
 Например, можно временно скрыть текст внутри <xref:Microsoft.Office.Tools.Word.Bookmark> (в настройке уровня документа) или <xref:Microsoft.Office.Interop.Word.Bookmark> (в надстройке VSTO) перед отправкой документа на принтере.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Скрытие текста в элементе управления Bookmark при печати документа  
  
1.  Создайте процедуру, которая скрывает весь текст в заданном диапазоне.  
  
     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]  
  
2.  Создайте процедуру, которая отменяет скрытие текста в заданном диапазоне.  
  
     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]  
  
3.  Передайте диапазон закладки в метод `HideText` , напечатайте документ, а затем передайте тот же диапазон в метод `UnhideText` .  
  
     Следующий пример кода можно использовать в настройке на уровне документа. Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]  
  
     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Данный пример кода предполагает, что документ содержит <xref:Microsoft.Office.Tools.Word.Bookmark> управления (в настройке уровня документа) или <xref:Microsoft.Office.Interop.Word.Bookmark> управления (в надстройке VSTO), которая называется `bookmark1`.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Программная печать документов](../vsto/how-to-programmatically-print-documents.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое руководство. Программно сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Практическое руководство. Программное обновление текста закладки](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
