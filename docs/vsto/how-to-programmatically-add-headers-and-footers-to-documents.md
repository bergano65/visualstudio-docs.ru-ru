---
title: Руководство. Программное добавление верхних и нижних колонтитулов в документы
description: Узнайте, как можно добавить текст в верхние и нижние колонтитулы в документе с помощью свойства Headers и Footer нижнего колонтитула раздела.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 63b50e020efa549993e36dbd5b43504467e554a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908602"
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Руководство. Программное добавление верхних и нижних колонтитулов в документы
  Для добавления текста в верхние и нижние колонтитулы в документе можно использовать свойство <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> и свойство <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> раздела <xref:Microsoft.Office.Interop.Word.Section>. Каждый раздел документа содержит три верхних и нижних колонтитула.

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>

- <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>

  Процедуры для настроек на уровне документа и надстроек VSTO отличаются друг от друга.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customizations"></a>Настройки уровня документа.
 Чтобы использовать следующие примеры кода, выполняйте их из класса `ThisDocument` в своем проекте.

### <a name="to-add-text-to-footers-in-the-document"></a>Добавление текста в нижние колонтитулы документа

1. Следующий пример кода задает шрифт текста, который необходимо вставить в основной нижний колонтитул каждого раздела документа, а затем вставляет текст в нижний колонтитул.

     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>Добавление текста в верхние колонтитулы документа

1. Следующий пример кода добавляет поле для отображения номера страницы в каждом верхнем колонтитуле документа, а затем устанавливает выравнивание абзаца, чтобы выровнять текст по правому краю верхнего колонтитула.

     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]

## <a name="vsto-add-ins"></a>Надстройки VSTO
 Чтобы использовать следующие примеры кода, выполняйте их из класса `ThisAddIn` в своем проекте.

### <a name="to-add-text-to-footers-in-a-document"></a>Добавление текста в нижние колонтитулы документа

1. Следующий пример кода задает шрифт текста, который необходимо вставить в основной нижний колонтитул каждого раздела документа, а затем вставляет текст в нижний колонтитул. В этом примере кода используется активный документ.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]

### <a name="to-add-text-to-headers-in-the-document"></a>Добавление текста в верхние колонтитулы документа

1. Следующий пример кода добавляет поле для отображения номера страницы в каждом верхнем колонтитуле документа, а затем устанавливает выравнивание абзаца, чтобы выровнять текст по правому краю верхнего колонтитула. В этом примере кода используется активный документ.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]

## <a name="see-also"></a>См. также раздел
- [Руководство. Программное создание новых документов](../vsto/how-to-programmatically-create-new-documents.md)
- [Руководство. программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Пошаговое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
