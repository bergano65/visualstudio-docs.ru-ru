---
title: Практическое руководство. Программное закрытие документов
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dd5e73a272243aeb2ddc38ea5c2f49bb1b62e6a0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598366"
---
# <a name="how-to-programmatically-close-documents"></a>Практическое руководство. Программное закрытие документов
  Можно закрыть активный документ или указать документ для закрытия.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>Закрыть активный документ
 Для закрытия активного документа можно использовать две процедуры: одну для настроек на уровне документа и одну для надстроек VSTO.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Закрытие активного документа в настройке на уровне документа

1.  Для закрытия документа, связанного с настройкой, вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Close%2A> класса `ThisDocument` в своем проекте. Чтобы использовать следующий пример кода, запустите его из класса `ThisDocument` .

    > [!NOTE]
    >  В этом примере значение <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> передается в параметр *SaveChanges* , чтобы закрыть окно без сохранения изменений или без вывода запросов пользователю.

     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Закрытие активного документа в надстройке VSTO

1.  Для закрытия активного документа вызовите метод <xref:Microsoft.Office.Interop.Word._Document.Close%2A> свойства <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> . Чтобы использовать следующий пример кода, выполните его из класса `ThisAddIn` в своем проекте.

    > [!NOTE]
    >  В этом примере значение <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> передается в параметр *SaveChanges* , чтобы закрыть окно без сохранения изменений или без вывода запросов пользователю.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]

## <a name="close-a-document-that-you-specify-by-name"></a>Процедура закрытия документа с заданным именем
 Процедура закрытия документа с заданным именем идентична процедуре для надстройки VSTO и настроек на уровне документа.

### <a name="to-close-a-document-that-you-specify-by-name"></a>Закрытие документа с заданным именем

1.  Укажите имя документа в качестве аргумента для коллекции <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> , а затем вызовите метод <xref:Microsoft.Office.Interop.Word._Document.Close%2A> . В приведенном ниже примере кода предполагается, что в Word открыт документ с именем **NewDocument** .

    > [!NOTE]
    >  В этом примере значение <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> передается в параметр *SaveChanges* , чтобы закрыть окно без сохранения изменений или без вывода запросов пользователю.

     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Программное Открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)
- [Практическое руководство. Программное сохранение документов](../vsto/how-to-programmatically-save-documents.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
