---
title: Руководство. программное скрытие текста в документах
description: Узнайте, как можно скрыть текст в документе Microsoft Word, установив свойство Hidden шрифта для определенного диапазона текста.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e74a7a48effafefdc945b0e86dbec6d9692dabd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885382"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Руководство. программное скрытие текста в документах
  Текст в документе можно скрыть, установив свойство <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> объекта <xref:Microsoft.Office.Interop.Word.Range.Font%2A> для определенного фрагмента текста.

 Например, можно временно скрыть текст в <xref:Microsoft.Office.Tools.Word.Bookmark> (в настройке уровня документа) или <xref:Microsoft.Office.Interop.Word.Bookmark> (в надстройке VSTO) перед отправкой документа на принтер.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Скрытие текста в элементе управления Bookmark при печати документа

1. Создайте процедуру, которая скрывает весь текст в заданном диапазоне.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. Создайте процедуру, которая отменяет скрытие текста в заданном диапазоне.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. Передайте диапазон закладки в метод `HideText` , напечатайте документ, а затем передайте тот же диапазон в метод `UnhideText` .

     Следующий пример кода можно использовать в настройке на уровне документа. Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>Компиляция кода
 В этом примере кода предполагается, что документ содержит <xref:Microsoft.Office.Tools.Word.Bookmark> элемент управления (в настройке уровня документа) или <xref:Microsoft.Office.Interop.Word.Bookmark> элемент управления (в надстройке VSTO) с именем `bookmark1` .

## <a name="see-also"></a>См. также раздел
- [Руководство. Программная печать документов](../vsto/how-to-programmatically-print-documents.md)
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Как программно сбрасывать диапазоны в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Руководство. Программное обновление текста закладок](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
