---
title: "Практическое руководство. Изменение размеров элементов управления Bookmark"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "элементы управления [разработка решений Office в Visual Studio], изменение размера"
  - "элемент управления Bookmark, изменение размера"
ms.assetid: 3de1c774-921a-4113-a54a-e3b8d4a65d53
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Практическое руководство. Изменение размеров элементов управления Bookmark
  Размер элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> задается при его добавлении в документ Microsoft Office Word. Его также можно изменить позднее.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Существует три способа изменения размера закладки.  
  
-   Добавление или удаление текста в элементе управления <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     При добавлении текста в закладку размер закладки автоматически увеличивается, чтобы вместить новый текст. При удалении текста размер закладки автоматически уменьшается.  
  
-   Изменение свойств <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>.и <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Это удобно, когда вы изменяете размер только на несколько символов.  
  
-   Повторное создание элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Это удобно, если нужно существенно изменить размер или положение закладки.  
  
 В проектах на уровне документа элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> можно добавлять в документ во время разработки или во время выполнения. В проектах надстроек VSTO вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в любой открытый документ во время выполнения. Для получения дополнительной информации см. [Практическое руководство. Добавление закладок в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Изменение свойств начала и окончания  
  
#### Изменение размера закладки в проекте уровня документа во время разработки  
  
1.  Выберите закладку в окне **Свойства**.  
  
2.  Увеличьте или уменьшите значение свойства <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A>.  
  
3.  Увеличьте или уменьшите значение свойства <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A>.  
  
#### Изменение размера закладки в проекте уровня документа во время выполнения  
  
1.  Измените свойства <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> и <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark>, созданного во время выполнения или во время разработки.  
  
     В следующем примере кода добавляется пять символов к началу закладки с именем `SampleBookmark`. В этом коде предполагается, что имеется по крайней мере пять символов текста до закладки.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#2)]  
  
     В следующем примере кода добавляется пять символов к концу той же закладки. В этом коде предполагается, что имеется по крайней мере пять символов текста после закладки.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#3)]  
  
#### Изменение размера закладки в проекте надстройки VSTO во время выполнения  
  
1.  Измените свойства <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> и <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark>, созданного во время выполнения.  
  
     В следующем примере кода создается объект <xref:Microsoft.Office.Tools.Word.Bookmark>, содержащий текст в первом абзаце активного документа, а затем удаляется по пять символов в начале и в конце <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#16)]
     [!code-vb[Trin_WordAddInDynamicControls#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#16)]  
  
## Повторное создание закладки  
 Вы можете изменить размер закладки в проекте уровня документа, добавив новую закладку с именем существующей закладки, но другого размера.  
  
#### Повторное создание закладки в проекте уровня документа во время разработки  
  
1.  Выделите текст для включения в новый элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
2.  В меню **Вставить** выберите пункт **Закладка**.  
  
3.  В диалоговом окне **Закладка** выберите имя закладки, размер которой требуется изменить, и нажмите кнопку **Добавить**.  
  
## См. также  
 [Практическое руководство. Добавление закладок в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Практическое руководство. Изменения размера элементов управления "NamedRange"](../vsto/how-to-resize-namedrange-controls.md)   
 [Практическое руководство. Изменение размера элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  