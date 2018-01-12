---
title: "Как: изменение размеров элементов управления Bookmark | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fc546ed1b840cc072510a49a16696a1bfc91cee7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-resize-bookmark-controls"></a>Практическое руководство. Изменение размеров элементов управления Bookmark
  Размер элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> задается при его добавлении в документ Microsoft Office Word. Его также можно изменить позднее.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Существует три способа изменения размера закладки.  
  
-   Добавление или удаление текста в элементе управления <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     При добавлении текста в закладку размер закладки автоматически увеличивается, чтобы вместить новый текст. При удалении текста размер закладки автоматически уменьшается.  
  
-   Изменение свойств <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .и <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Это удобно, когда вы изменяете размер только на несколько символов.  
  
-   Повторное создание элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Это удобно, если нужно существенно изменить размер или положение закладки.  
  
 В проектах на уровне документа элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> можно добавлять в документ во время разработки или во время выполнения. В проектах надстроек VSTO вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в любой открытый документ во время выполнения. Для получения дополнительной информации см. [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="changing-the-start-and-end-properties"></a>Изменение свойств начала и окончания  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Изменение размера закладки в проекте уровня документа во время разработки  
  
1.  Выберите закладку в окне **Свойства** .  
  
2.  Увеличьте или уменьшите значение свойства <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .  
  
3.  Увеличьте или уменьшите значение свойства <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> .  
  
#### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Изменение размера закладки в проекте уровня документа во время выполнения  
  
1.  Измените свойства <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> и <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> , созданного во время выполнения или во время разработки.  
  
     В следующем примере кода добавляется пять символов к началу закладки с именем `SampleBookmark`. В этом коде предполагается, что имеется по крайней мере пять символов текста до закладки.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     В следующем примере кода добавляется пять символов к концу той же закладки. В этом коде предполагается, что имеется по крайней мере пять символов текста после закладки.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
#### <a name="to-resize-a-bookmark-in-an-vsto-add-in-project-at-run-time"></a>Изменение размера закладки в проекте надстройки VSTO во время выполнения  
  
1.  Измените свойства <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> и <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> , созданного во время выполнения.  
  
     В следующем примере кода создается объект <xref:Microsoft.Office.Tools.Word.Bookmark> , содержащий текст в первом абзаце активного документа, а затем удаляется по пять символов в начале и в конце <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreating-the-bookmark"></a>Повторное создание закладки  
 Вы можете изменить размер закладки в проекте уровня документа, добавив новую закладку с именем существующей закладки, но другого размера.  
  
#### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Повторное создание закладки в проекте уровня документа во время разработки  
  
1.  Выделите текст для включения в новый элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
2.  В меню **Вставить** выберите пункт **Закладка**.  
  
3.  В диалоговом окне **Закладка** выберите имя закладки, размер которой требуется изменить, и нажмите кнопку **Добавить**.  
  
## <a name="see-also"></a>См. также  
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Как: изменение размеров элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Как: изменение размеров элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  