---
title: Руководство. Программное форматирование текста в документах
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 76af290b0e32126689dbe7b60f27889d9742ea7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519851"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Руководство. Программное форматирование текста в документах
  Вы можете использовать объект <xref:Microsoft.Office.Interop.Word.Range> для форматирования текста в документе Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Следующий пример выделяет первый абзац в документе и изменяет размер шрифта, имя шрифта и тип выравнивания. Затем он выбирает диапазон и отображает окно сообщения о приостановке перед выполнением следующего раздела кода. В следующем разделе вызывается метод Undo <xref:Microsoft.Office.Tools.Word.Document> ведущего элемента (для настройки на уровне документа) или <xref:Microsoft.Office.Interop.Word.Document> класса (для надстройки VSTO) три раза. Применяется стиль «Обычный отступ» и отображается окно сообщения о приостановке выполнения кода. Затем код вызывает метод <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> один раз и показывает окно сообщения.

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="to-format-text-using-a-document-level-customization"></a>Форматирование текста с помощью настройки на уровне документа

1. Следующий пример можно использовать в настройке на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Форматирование текста с использованием надстройки VSTO

1. Следующий пример можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>См. также раздел
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Инструкции. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Руководство. Программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
