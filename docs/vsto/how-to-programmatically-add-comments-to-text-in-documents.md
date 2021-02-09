---
title: Руководство. Программное добавление комментариев к тексту в документах
description: Программное добавление комментариев к тексту в документах. Свойство Comments класса Document добавляет комментарий к диапазону текста в документе Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f5f0fba5169be71718993fbc271faf64fdac9fb1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918481"
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

## <a name="see-also"></a>См. также раздел
- [Руководство. Программное удаление всех комментариев из документов](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Ведущий элемент документа](../vsto/document-host-item.md)
