---
title: Практическое руководство. Программное расширение диапазонов в документах
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26213477e7cec69da9171c5197371772973be5d3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812755"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Практическое руководство. Программное расширение диапазонов в документах
  После определения объекта <xref:Microsoft.Office.Interop.Word.Range> в документе Microsoft Office Word вы изменяете его начальную и конечную точки с помощью методов <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> и <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . Методы <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> и <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> принимают те же два аргумента, *Unit* и *Count*. Методы *Count* — это количество единиц для перемещения, и аргумент *Unit* может иметь одно из следующих <xref:Microsoft.Office.Interop.Word.WdUnits> значений:

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  В следующем примере определяется диапазон в семь символов. Затем начальная позиция этого диапазона перемещается на семь символов после исходной начальной позиции. Поскольку конечная позиция диапазона также находится через семь символов после начальной позиции, результатом является диапазон, состоящий из нуля символов. Затем код перемещает конечную позицию на семь символов после текущей конечной позиции.

## <a name="to-extend-a-range"></a>Расширение диапазона

1. Определите диапазон символов. Дополнительные сведения см. в разделе [Как Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

     Следующий пример кода можно использовать в настройке на уровне документа.

     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]

2. Используйте метод <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> , чтобы переместить начальную позицию диапазона.

     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]

3. Используйте метод <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> , чтобы переместить конечную позицию диапазона.

     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]

## <a name="document-level-customization-code"></a>Код настройки уровня документа

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Расширение диапазона в настройке на уровне документа

1. В следующем примере показан полный код для настройки на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]

## <a name="vsto-add-in-code"></a>Код надстройки VSTO

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Расширение диапазона в надстройке VSTO уровня приложения

1. В следующем примере показан полный код для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Программно сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Практическое руководство. Программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Практическое руководство. Извлечение знаков начала и завершения в диапазонах программным способом](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Практическое руководство. Программно exclude абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
