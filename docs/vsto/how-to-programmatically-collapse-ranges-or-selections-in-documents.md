---
title: Программное свертывание диапазонов и выделений в документах
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7394e8703f0437493536655e11b00ed302e59cff
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402237"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Практическое руководство. Программное свертывание диапазонов и выделений в документах
  Если вы работаете с объектом <xref:Microsoft.Office.Interop.Word.Range> или <xref:Microsoft.Office.Interop.Word.Selection> , может потребоваться изменить выделение на точку вставки перед вставкой текста, чтобы избежать перезаписи существующего текста. Как <xref:Microsoft.Office.Interop.Word.Range> и <xref:Microsoft.Office.Interop.Word.Selection> объекты имеют свернуть метод, который использует <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> значений перечисления:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> сворачивает выделение к началу выделения. Это значение по умолчанию, если не указано значение перечисления.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> сворачивает выделение к концу выделения.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Сворачивание диапазона и вставка нового текста

1. Создайте объект <xref:Microsoft.Office.Interop.Word.Range> , состоящий из первого абзаца в документе.

    Следующий пример кода можно использовать в настройке на уровне документа.

    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]

    Следующий пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]

2. Используйте значение перечисления <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> для сворачивания диапазона.

    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]

3. Вставьте новый текст.

    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]

4. Выберите <xref:Microsoft.Office.Interop.Word.Range>.

    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]

   Если вы используете значение перечисления <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , текст вставляется в начало следующего абзаца.

   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]

   Можно предположить, что вставка нового предложения выполняется перед символом абзаца, но это не так, поскольку исходный диапазон включает символ абзаца. Дополнительные сведения см. в разделе [Практическое руководство. Программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Пример настройки на уровне документа

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Сворачивание диапазона в настройке на уровне документа

1. В следующем примере показан полный метод для настройки на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]

## <a name="vsto-add-in-example"></a>Пример надстройки VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Сворачивание диапазона в надстройке VSTO

1. В следующем примере показан полный метод для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Программная Вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Практическое руководство. Извлечение знаков начала и завершения в диапазонах программным способом](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Практическое руководство. Программно exclude абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Практическое руководство. Программно сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
