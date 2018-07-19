---
title: 'Практическое: программное форматирование текста в документах'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: baf6f49b0347aa4a770b4f7a47c7fa8195d5ede5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257414"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Практическое: программное форматирование текста в документах
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
 [Практическое: программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое: программная Вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Практическое: программными средствами поиска и замены текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  