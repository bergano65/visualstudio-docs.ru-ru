---
title: "Как: программное добавление примечаний в текст документа | Документы Microsoft"
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
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
ms.assetid: 4e396e31-01bf-424c-be6b-9a1806bcd572
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 69f320ef3e7b3914d9d6eadb7466b3a216ef95d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Практическое руководство. Программное добавление примечаний в текст документа
  Свойство комментарии класса документа добавляет комментарий к диапазону текста в документе Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 В следующем примере комментарий добавляется в первый абзац документа.  
  
### <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Добавление нового комментария в текст в настройке уровня документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> свойства <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> и укажите диапазон и текст комментария. Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
### <a name="to-add-a-new-comment-to-text-in-an-vsto-add-in"></a>Добавление нового комментария в текст в надстройке VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> свойства <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> и укажите диапазон и текст комментария.  
  
     В следующем примере кода добавляется комментарий в активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Для изменения инициалов пользователя, добавляемых Word в комментарии, используйте свойство <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .  
  
## <a name="see-also"></a>См. также  
 [Как: программное удаление всех комментариев из документа](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)  
  
  