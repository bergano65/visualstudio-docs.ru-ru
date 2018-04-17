---
title: 'Как: программное удаление всех комментариев из документа | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 19c713356a8949261524eda9f44fee8fae9f9f21
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
  