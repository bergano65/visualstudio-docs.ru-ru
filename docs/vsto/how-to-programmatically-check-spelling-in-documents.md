---
title: 'Как: Программная проверка орфографии в документах | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a7445b48dc936bf57a5c93426e9ffcc7f114eb32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Практическое руководство. Программная проверка правописания в документах
  Чтобы проверить орфографию в документе, используйте <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> метод. Этот метод возвращает логическое значение, указывающее, предоставленный параметр написано правильно.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Проверка правописания и отображение результатов в окне сообщения  
  
1.  Вызовите <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> метод и передайте ему диапазон текста на наличие орфографических ошибок. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  