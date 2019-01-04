---
title: Как выполнить Программная проверка правописания в документах
ms.date: 02/02/2017
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
ms.openlocfilehash: d300d51d6c244623ff330c5fa443c6a332d6c3f9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942917"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Как выполнить Программная проверка правописания в документах
  Чтобы проверить орфографию в документе, используйте <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> метод. Этот метод возвращает логическое значение, указывающее, предоставленным параметром написано правильно.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Проверка правописания и отображение результатов в окне сообщения  
  
1.  Вызовите <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> метод и передать его диапазон текста на наличие орфографических ошибок. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
