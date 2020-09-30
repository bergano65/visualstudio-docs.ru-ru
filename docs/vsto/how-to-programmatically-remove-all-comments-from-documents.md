---
title: Руководство. Программное удаление всех комментариев из документов
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee30cb7d4083adfff18261e3267dea1d8a96626f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584824"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Руководство. Программное удаление всех комментариев из документов
  Используйте метод `DeleteAllComments` для удаления всех комментариев из документа Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Удаление всех комментариев из документа в рамках настройки на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> класса `ThisDocument` в проекте. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` .

     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Удаление всех комментариев из документа с помощью надстройки VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> документа <xref:Microsoft.Office.Interop.Word.Document> , из которого нужно удалить комментарии.

     В приведенном ниже примере кода из активного документа удаляются все комментарии. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]

## <a name="see-also"></a>См. также
- [Руководство. Программное добавление комментариев к тексту в документах](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [Ведущий элемент документа](../vsto/document-host-item.md)
