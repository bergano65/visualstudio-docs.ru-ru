---
title: Как изменить размер элементов управления Bookmark
description: Узнайте, как с помощью Visual Studio задать размер элемента управления Bookmark при его добавлении в документ Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 55fe398b277586404c91ef7cb172f7ce3a9c98ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927851"
---
# <a name="how-to-resize-bookmark-controls"></a>Как изменить размер элементов управления Bookmark
  Размер элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> задается при его добавлении в документ Microsoft Office Word. Его также можно изменить позднее.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Существует три способа изменения размера закладки.

- Добавление или удаление текста в элементе управления <xref:Microsoft.Office.Tools.Word.Bookmark> .

   При добавлении текста в закладку размер закладки автоматически увеличивается, чтобы вместить новый текст. При удалении текста размер закладки автоматически уменьшается.

- Изменение свойств <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .и <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> .

   Это удобно, когда вы изменяете размер только на несколько символов.

- Повторное создание элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> .

   Это удобно, если нужно существенно изменить размер или положение закладки.

  В проектах на уровне документа элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> можно добавлять в документ во время разработки или во время выполнения. В проектах надстроек VSTO вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в любой открытый документ во время выполнения. Дополнительные сведения см. [в разделе руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="change-the-start-and-end-properties"></a>Изменение свойств начала и окончания

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Изменение размера закладки в проекте уровня документа во время разработки

1. Выберите закладку в окне **Свойства** .

2. Увеличьте или уменьшите значение свойства <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .

3. Увеличьте или уменьшите значение свойства <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> .

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Изменение размера закладки в проекте уровня документа во время выполнения

1. Измените свойства <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> и <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> , созданного во время выполнения или во время разработки.

     В следующем примере кода добавляется пять символов к началу закладки с именем `SampleBookmark`. В этом коде предполагается, что имеется по крайней мере пять символов текста до закладки.

     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]

     В следующем примере кода добавляется пять символов к концу той же закладки. В этом коде предполагается, что имеется по крайней мере пять символов текста после закладки.

     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]

### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-run-time"></a>Изменение размера закладки в проекте надстройки VSTO во время выполнения

1. Измените свойства <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> и <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> , созданного во время выполнения.

     В следующем примере кода создается объект <xref:Microsoft.Office.Tools.Word.Bookmark> , содержащий текст в первом абзаце активного документа, а затем удаляется по пять символов в начале и в конце <xref:Microsoft.Office.Tools.Word.Bookmark>.

     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]

## <a name="recreate-the-bookmark"></a>Повторное создание закладки
 Вы можете изменить размер закладки в проекте уровня документа, добавив новую закладку с именем существующей закладки, но другого размера.

### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Повторное создание закладки в проекте уровня документа во время разработки

1. Выделите текст для включения в новый элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> .

2. В меню **Вставить** выберите пункт **Закладка**.

3. В диалоговом окне **Закладка** выберите имя закладки, размер которой требуется изменить, и нажмите кнопку **Добавить**.

## <a name="see-also"></a>См. также раздел
- [Руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Как изменить размер элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Как изменить размер элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
