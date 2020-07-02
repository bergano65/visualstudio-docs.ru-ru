---
title: Руководство. Программное добавление комментариев к тексту в документах
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88350a0fb50c1d5feb0eba9706ef5b6ad56fd9df
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538117"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Руководство. Программное добавление комментариев к тексту в документах
  Свойство Comments класса Document добавляет комментарий к диапазону текста в Microsoft Office документе Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 В следующем примере комментарий добавляется в первый абзац документа.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Добавление нового комментария в текст в настройке уровня документа

1. Вызовите метод <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> свойства <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> и укажите диапазон и текст комментария. Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Добавление нового комментария к тексту в надстройке VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> свойства <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> и укажите диапазон и текст комментария.

     В следующем примере кода добавляется комментарий в активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]

## <a name="robust-programming"></a>Отказоустойчивость
 Для изменения инициалов пользователя, добавляемых Word в комментарии, используйте свойство <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .

## <a name="see-also"></a>См. также
- [Руководство. Программное удаление всех комментариев из документов](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Ведущий элемент документа](../vsto/document-host-item.md)
