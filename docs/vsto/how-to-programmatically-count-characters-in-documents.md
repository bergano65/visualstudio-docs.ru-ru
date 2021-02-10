---
title: Руководство. Программный подсчет символов в документах
description: Узнайте, как можно определить количество символов в документе с помощью свойства Count коллекции символов.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fda6d3bb553470a914d55fa5aa24d1db8b2365e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964164"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Руководство. Программный подсчет символов в документах
  Первый знак в документ находится в позиции 0, которая представляет точку вставки. Позиция последнего знака равна общему количеству знаков в документе. Число знаков в документе можно определить с помощью свойства <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> коллекции <xref:Microsoft.Office.Interop.Word.Characters> .

 Учитываются все знаки в документе, включая пробелы, знаки абзацев и другие знаки, которые обычно скрыты. Даже новый пустой документ возвращает значение 1, так как он содержит знак абзаца.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Отображение числа знаков в настройке уровня документа

1. Выделите весь документ.

     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]

2. Отобразите количество знаков в документе в окне сообщения.

     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Отображение числа символов в надстройке VSTO

1. Выделите весь документ. В следующем примере кода выбирается активный документ.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]

2. Отобразите количество знаков в документе в окне сообщения.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]

## <a name="see-also"></a>См. также раздел
- [Как программно получить начальные и конечные символы в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
