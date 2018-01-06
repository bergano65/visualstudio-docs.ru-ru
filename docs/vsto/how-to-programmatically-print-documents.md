---
title: "Как: программная печать документов | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ec4808adeb38d0ee8cf13d28e181260fbbae95bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-print-documents"></a>Практическое руководство. Программная печать документов
  Вы можете распечатать весь документ Microsoft Office Word или часть документа, на принтере по умолчанию.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="printing-a-document-that-is-part-of-a-document-level-customization"></a>Печать документа, который является частью настройки уровня документа  
  
#### <a name="to-print-the-entire-document"></a>Печать всего документа  
  
1.  Чтобы напечатать весь документ, вызовите в своем проекте метод <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> класса `ThisDocument` . Чтобы использовать этот пример, запустите код из класса `ThisDocument` .  
  
     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]  
  
#### <a name="to-print-the-current-page-of-the-document"></a>Печать текущей страницы документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> класса `ThisDocument` в своем проекте и укажите, что необходимо напечатать одну копию текущей страницы. Чтобы использовать этот пример, запустите код из класса `ThisDocument` .  
  
     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]  
  
## <a name="printing-a-document-by-using-an-vsto-add-in"></a>Печать документа с помощью надстройки VSTO  
  
#### <a name="to-print-an-entire-document"></a>Печать всего документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> документа <xref:Microsoft.Office.Interop.Word.Document> , который требуется напечатать. В следующем примере кода печатается активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]  
  
#### <a name="to-print-the-current-page-of-a-document"></a>Печать текущей страницы документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> класса <xref:Microsoft.Office.Interop.Word.Document> объекта, который требуется напечатать, и укажите, что необходимо напечатать одну копию текущей страницы. В следующем примере кода печатается активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]  
  
## <a name="see-also"></a>См. также  
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  