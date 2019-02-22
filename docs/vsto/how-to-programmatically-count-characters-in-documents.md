---
title: Практическое руководство. Программным способом подсчета символов в документах
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c9e5dd79465301e5d2e6362daf70ef3e5b7c54ee
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646321"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Практическое руководство. Программным способом подсчета символов в документах
  Первый знак в документ находится в позиции 0, которая представляет точку вставки. Позиция последнего знака равна общему количеству знаков в документе. Число знаков в документе можно определить с помощью свойства <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> коллекции <xref:Microsoft.Office.Interop.Word.Characters> .

 Учитываются все знаки в документе, включая пробелы, знаки абзацев и другие знаки, которые обычно скрыты. Даже новый пустой документ возвращает значение 1, так как он содержит знак абзаца.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Отображение числа знаков в настройке уровня документа

1.  Выделите весь документ.

     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]

2.  Отобразите количество знаков в документе в окне сообщения.

     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Чтобы отобразить число знаков в надстройке VSTO

1.  Выделите весь документ. В следующем примере кода выбирается активный документ.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]

2.  Отобразите количество знаков в документе в окне сообщения.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Извлечение знаков начала и завершения в диапазонах программным способом](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
