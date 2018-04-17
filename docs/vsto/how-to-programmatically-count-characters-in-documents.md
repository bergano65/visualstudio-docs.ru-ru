---
title: 'Как: программный подсчет символов в документах | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ae05466c871b51d790f1031755be062806fc120
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Практическое руководство. Программный подсчет символов в документах
  Первый знак в документ находится в позиции 0, которая представляет точку вставки. Позиция последнего знака равна общему количеству знаков в документе. Число знаков в документе можно определить с помощью свойства <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> коллекции <xref:Microsoft.Office.Interop.Word.Characters> .  
  
 Учитываются все знаки в документе, включая пробелы, знаки абзацев и другие знаки, которые обычно скрыты. Даже новый пустой документ возвращает значение 1, так как он содержит знак абзаца.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Отображение числа знаков в настройке уровня документа  
  
1.  Выделите весь документ.  
  
     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]  
  
2.  Отобразите количество знаков в документе в окне сообщения.  
  
     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]  
  
### <a name="to-display-the-number-of-characters-in-an-vsto-add-in"></a>Отображение числа знаков в надстройке VSTO  
  
1.  Выделите весь документ. В следующем примере кода выбирается активный документ.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]  
  
2.  Отобразите количество знаков в документе в окне сообщения.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное извлечение символов начала и завершения в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  