---
title: Практическое руководство. Программное форматирование текста в документах
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 66ca84d2246a3335aa3a1bbc0900ca6f48f59f01
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630695"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Практическое руководство. Программное форматирование текста в документах
  Вы можете использовать объект <xref:Microsoft.Office.Interop.Word.Range> для форматирования текста в документе Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Следующий пример выделяет первый абзац в документе и изменяет размер шрифта, имя шрифта и тип выравнивания. Затем он выбирает диапазон и отображает окно сообщения о приостановке перед выполнением следующего раздела кода. Следующий раздел вызывает метод отмены <xref:Microsoft.Office.Tools.Word.Document> ведущего элемента (для настройки уровня документа) или <xref:Microsoft.Office.Interop.Word.Document> класса (для надстройки VSTO) три раза. Применяется стиль «Обычный отступ» и отображается окно сообщения о приостановке выполнения кода. Затем код вызывает метод <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> один раз и показывает окно сообщения.

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="to-format-text-using-a-document-level-customization"></a>Форматирование текста с помощью настройки на уровне документа

1.  Следующий пример можно использовать в настройке на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Форматирование текста с использованием надстройки VSTO

1.  Следующий пример можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Практическое руководство. Программная Вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Практическое руководство. Программным способом поиска и замены текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
