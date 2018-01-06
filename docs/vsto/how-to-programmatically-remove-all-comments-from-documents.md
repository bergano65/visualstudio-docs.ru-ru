---
title: "Как: программное удаление всех комментариев из документа | Документы Microsoft"
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
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f22dd675cd6e247f2f6fd6c17f69ea6370230aa0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Практическое руководство. Программное удаление всех комментариев из документа
  Метод DeleteAllComments удаление всех комментариев из документа Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Удаление всех комментариев из документа в рамках настройки на уровне документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> класса `ThisDocument` в проекте. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` .  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
### <a name="to-remove-all-comments-from-a-document-by-using-an-vsto-add-in"></a>Удаление всех комментариев из документа с помощью надстройки VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> документа <xref:Microsoft.Office.Interop.Word.Document> , из которого нужно удалить комментарии.  
  
     В приведенном ниже примере кода из активного документа удаляются все комментарии. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное добавление примечаний в текст документа](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)  
  
  