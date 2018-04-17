---
title: 'Как: программное скрытие текста в документах | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b8e2ea2f5f8af3876fe64d90d5f2d77874ebb252
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Практическое руководство. Программное скрытие текста в документах
  Текст в документе можно скрыть, установив свойство <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> объекта <xref:Microsoft.Office.Interop.Word.Range.Font%2A> для определенного фрагмента текста.  
  
 Например, можно временно скрыть текст в элементе <xref:Microsoft.Office.Tools.Word.Bookmark> (в настройке на уровне документа) или в элементе <xref:Microsoft.Office.Interop.Word.Bookmark> (в надстройке VSTO) перед отправкой документа в печать.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Скрытие текста в элементе управления Bookmark при печати документа  
  
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
  
     Приведенный ниже пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 В этом примере кода предполагается, что документ содержит элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> (в настройке на уровне документа) или элемент управления <xref:Microsoft.Office.Interop.Word.Bookmark> (в надстройке VSTO) с именем `bookmark1`.  
  
## <a name="see-also"></a>См. также  
 [Как: программная печать документов](../vsto/how-to-programmatically-print-documents.md)   
 [Как: программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Как: программным образом сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Как: программное обновление текста закладки](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  