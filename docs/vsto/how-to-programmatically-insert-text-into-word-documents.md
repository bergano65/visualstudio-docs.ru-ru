---
title: Инструкции. Программная вставка текста в документы Word
description: Сведения о программной вставке текста в документ Microsoft Word с помощью Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e82aef0fc473b0ed11bcc9fce15b6426d5b91b4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885395"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Инструкции. Программная вставка текста в документы Word
  Существует три основных способа вставки текста в документы Microsoft Office Word:

- вставка текста в диапазон;

- замена текста в диапазоне на новый текст;

- использование метода <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> объекта <xref:Microsoft.Office.Interop.Word.Selection> для вставки текста в позиции курсора или выделения.

> [!NOTE]
> Вы также можете вставить текст в элементы управления содержимым и закладки. Дополнительные сведения см. в разделе [элементы управления содержимым](../vsto/content-controls.md) и [элемент управления Bookmark](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Вставить текст в диапазон
 Используйте свойство <xref:Microsoft.Office.Interop.Word.Range.Text%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> для вставки текста в документ.

### <a name="to-insert-text-in-a-range"></a>Вставка текста в диапазон

1. Укажите диапазон в начале документа и вставьте текст **New Text**.

     Следующий пример кода можно использовать в настройке на уровне документа.

     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]

2. Выберите объект <xref:Microsoft.Office.Interop.Word.Range> , который был расширен от одного символа до длины вставленного текста.

     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]

## <a name="replace-text-in-a-range"></a>Замена текста в диапазоне
 Если указанный диапазон содержит текст, весь текст в диапазоне заменяется на вставленный текст.

### <a name="to-replace-text-in-a-range"></a>Замена текста в диапазоне

1. Создайте объект <xref:Microsoft.Office.Interop.Word.Range> , состоящий из первых 12 символов в документе.

     Следующий пример кода можно использовать в настройке на уровне документа.

     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]

2. Замените эти символы строкой **New Text**.

     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]

3. Выберите диапазон.

     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]

## <a name="insert-text-using-typetext"></a>Вставка текста с помощью TypeText
 Метод <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> вставляет текст в выделение. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> ведет себя по-разному в зависимости от параметров, заданных на компьютере пользователя. Код в следующей процедуре объявляет объектную переменную <xref:Microsoft.Office.Interop.Word.Selection> , а также отключает параметр **Overtype** , если он включен. Если параметр **Overtype** включен, любой текст рядом с курсором будет перезаписан.

### <a name="to-insert-text-using-the-typetext-method"></a>Вставка текста с помощью метода TypeText

1. Объявите переменную объекта <xref:Microsoft.Office.Interop.Word.Selection>.

    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]

2. Отключите параметр **Overtype** , если он включен.

    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]

3. Проверьте, находится ли текущее выделение у точки вставки.

    Если это так, код вставляет предложение с помощью <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>, а затем знак абзаца с помощью метода <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> .

    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]

4. Код в блоке **ElseIf** проверяет, является ли выделение обычным блоком выделения. Если это так, другой блок **If** проверяет, включен ли параметр **ReplaceSelection** . Если это так, код использует метод <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> выделения, чтобы свернуть его до точки вставки в начале выделенного блока текста. Вставьте текст и знак абзаца.

    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]

5. Если выделение не является точкой вставки или блоком выделенного текста, код в блоке **Else** не выполняет никаких действий.

    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]

   Можно также использовать <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> метод <xref:Microsoft.Office.Interop.Word.Selection> объекта, который имитирует функциональность клавиши **Backspace** на клавиатуре. Но когда дело доходит до вставки и изменения текста, объект <xref:Microsoft.Office.Interop.Word.Range> предоставляет больше возможностей для управления.

   В следующем примере показан полный код. Чтобы использовать этот пример, запустите код из класса `ThisDocument` или `ThisAddIn` в своем проекте.

   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]

## <a name="see-also"></a>См. также раздел
- [Руководство. Программное форматирование текста в документах](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Руководство. программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
