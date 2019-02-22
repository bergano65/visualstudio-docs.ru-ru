---
title: Практическое руководство. Программное определение и выделение диапазонов в документах
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d95690af1b1712aa374a4e9717c8c3bc6ac17fed
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599912"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Практическое руководство. Программное определение и выделение диапазонов в документах
  Вы можете определить диапазон в документе Microsoft Office Word с помощью объекта <xref:Microsoft.Office.Interop.Word.Range>. Можно выбрать весь документ несколькими способами, например, с помощью <xref:Microsoft.Office.Interop.Word.Range.Select%2A> метод <xref:Microsoft.Office.Interop.Word.Range> объекта, или с помощью свойства Content <xref:Microsoft.Office.Tools.Word.Document> класса (в настройке уровня документа) или <xref:Microsoft.Office.Interop.Word.Document> класса (в VSTO Add-in).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Определение диапазона
 В следующем примере показано, как создать объект <xref:Microsoft.Office.Interop.Word.Range>, включающий первые семь символов в активном документе, в том числе непечатаемые символы. Затем выполняется выбор текста в пределах диапазона.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Определение диапазона в настройке на уровне документа

1.  Добавьте диапазон в документ, передав начальный и последний символ в метод <xref:Microsoft.Office.Tools.Word.Document.Range%2A> класса <xref:Microsoft.Office.Tools.Word.Document>. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Определение диапазона с помощью надстройки VSTO

1.  Добавьте диапазон в документ, передав начальный и последний символ в метод <xref:Microsoft.Office.Interop.Word._Document.Range%2A> класса <xref:Microsoft.Office.Interop.Word.Document>. Следующий пример кода добавляет диапазон в активный документ. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]

## <a name="select-a-range-in-a-document-level-customization"></a>Выбор диапазона в настройке уровня документа
 В следующих примерах показано, как выделить весь документ с помощью метода <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> или с помощью свойства <xref:Microsoft.Office.Tools.Word.Document.Content%2A> класса <xref:Microsoft.Office.Tools.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Выбор всего документа как диапазона с помощью метода Select

1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>, который содержит весь документ. Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Выбор всего документа как диапазона с помощью свойства Content

1. Используйте свойство <xref:Microsoft.Office.Tools.Word.Document.Content%2A>, чтобы определить диапазон, который содержит весь документ.

    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]

   Для определения диапазона также можно использовать методы и свойства других объектов.

### <a name="to-select-a-sentence-in-the-active-document"></a>Выделение предложения в активном документе

1. Задайте диапазон с помощью коллекции <xref:Microsoft.Office.Interop.Word.Sentences>. Используйте индекс предложения, которое нужно выбрать.

    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]

   Еще один способ выделения предложения состоит в том, чтобы вручную установить начальное и конечное значение для диапазона.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Выделение предложения вручную с помощью установки начального и конечного значений

1.  Создайте переменную диапазона.

     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]

2.  Проверьте, есть ли по крайней мере два предложения в документе, задайте *запустить* и *окончания* аргументы из диапазона, а затем выберите диапазон.

     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Выберите диапазон с помощью надстройки VSTO
 В следующих примерах показано, как выделить весь документ с помощью метода <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> или с помощью свойства <xref:Microsoft.Office.Interop.Word._Document.Content%2A> класса <xref:Microsoft.Office.Interop.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Выбор всего документа как диапазона с помощью метода Select

1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>, который содержит весь документ. Следующий пример кода выделяет содержимое активного документа. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Выбор всего документа как диапазона с помощью свойства Content

1. Используйте свойство <xref:Microsoft.Office.Interop.Word._Document.Content%2A>, чтобы определить диапазон, который содержит весь документ.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]

   Для определения диапазона также можно использовать методы и свойства других объектов.

### <a name="to-select-a-sentence-in-the-active-document"></a>Выделение предложения в активном документе

1. Задайте диапазон с помощью коллекции <xref:Microsoft.Office.Interop.Word.Sentences>. Используйте индекс предложения, которое нужно выбрать.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]

   Еще один способ выделения предложения состоит в том, чтобы вручную установить начальное и конечное значение для диапазона.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Выделение предложения вручную с помощью установки начального и конечного значений

1.  Создайте переменную диапазона.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]

2.  Проверьте, есть ли по крайней мере два предложения в документе, задайте *запустить* и *окончания* аргументы из диапазона, а затем выберите диапазон.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]

## <a name="see-also"></a>См. также
- [Обзор объектной модели Word](../vsto/word-object-model-overview.md)
- [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Практическое руководство. Извлечение знаков начала и завершения в диапазонах программным способом](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Практическое руководство. Программно сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Практическое руководство. Программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Практическое руководство. Программно exclude абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
