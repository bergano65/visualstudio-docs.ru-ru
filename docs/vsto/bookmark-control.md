---
title: "Bookmark-элемент управления | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
ms.assetid: 940bf165-18c9-4db8-a46c-aad786b8bbad
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d846c1a0a52011991d231e567c1727e456a1feee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="bookmark-control"></a>Bookmark - элемент управления
  Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> представляет собой закладку с уникальным именем, которая предоставляет события и может быть привязана к данным. Закладка может использоваться как заполнитель для пометки элемента или расположения в документе Microsoft Office Word. Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> представляет собой комбинацию объектов <xref:Microsoft.Office.Interop.Word.Bookmark> и <xref:Microsoft.Office.Interop.Word.Range> .  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 В проектах на уровне документа вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документ во время разработки или во время выполнения. В проектах надстроек VSTO вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в любой открытый документ во время выполнения. Для получения дополнительной информации см. [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
## <a name="binding-data-to-the-control"></a>Привязка данных к элементу управления  
 Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> поддерживает простую привязку данных. Закладка должна быть привязана к источнику данных с помощью свойства <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . Свойство <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> — это свойство привязки данных по умолчанию для закладки.  
  
 Если данные в привязанном наборе данных обновляются, элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> отражает эти изменения.  
  
 В проектах на уровне документа вы также можете привязывать данные к закладкам с помощью окна **Источники данных** . Для получения дополнительной информации см. [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
## <a name="formatting"></a>Форматирование  
 Любое форматирование, которое можно применить к <xref:Microsoft.Office.Interop.Word.Bookmark> , также можно применить и к элементу управления <xref:Microsoft.Office.Tools.Word.Bookmark> . Сюда входят шрифты, отступы, интервалы, нумерация и стили.  
  
## <a name="assigning-text-to-the-bookmark"></a>Назначение текста закладке  
 Дополнительное различие между объектом <xref:Microsoft.Office.Interop.Word.Bookmark> и элементом управления <xref:Microsoft.Office.Tools.Word.Bookmark> состоит в их поведении при назначении текста закладке. Если вы назначаете текст <xref:Microsoft.Office.Interop.Word.Bookmark>нулевой длины, этот текст добавляется справа от закладки, а закладка останется нулевой длины. Однако если вы назначаете текст <xref:Microsoft.Office.Tools.Word.Bookmark>нулевой длины, этот текст вставляется в закладку, и длина закладки увеличивается на число вставленных символов.  
  
 Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> также имеет свойство <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> . Оно отличается от свойства <xref:Microsoft.Office.Interop.Word.Range.Text%2A> , которое доступно в свойстве <xref:Microsoft.Office.Tools.Word.Bookmark.Range%2A> элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> или в свойстве <xref:Microsoft.Office.Interop.Word.Bookmark.Range%2A> объекта <xref:Microsoft.Office.Interop.Word.Bookmark> .  
  
|Свойство Text|Описание|  
|-------------------|-----------------|  
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>|Используйте это свойство для отображения текста в закладке и оставления закладки в документе. Назначение текста закладке расширяет диапазон закладки и не удаляет ее.<br /><br /> Например, `Bookmark1.Text = "Hello world"` вставляет текст в закладку и оставляет закладку неизменной.|  
|<xref:Microsoft.Office.Interop.Word.Range.Text%2A>|Используйте это свойство для отображения текста в расположении закладки и автоматического удаления ее. Например, `Bookmark1.Range.Text = "Hello world"` вставляет текст в закладку и удаляет закладку.|  
  
## <a name="renaming-the-control-at-design-time"></a>Переименование элемента управления во время разработки  
 В проектах уровня документа при перетаскивании элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> из **панели элементов** в документ Visual Studio автоматически создает имя для этого элемента управления. Вы можете изменить это имя в окне **Свойства** .  
  
## <a name="overlapping-controls"></a>Перекрывающиеся элементы управления  
 Элементы управления Bookmark могут пересекаться друг с другом, т. е. один и тот же текст может совместно использоваться несколькими закладками. При назначении нового текста одной из перекрывающихся закладок она будет содержать только новый текст, и закладки больше не будут перекрываться. Другая закладка теперь будет содержать только текст, который не использовался совместно исходными перекрывающимися закладками.  
  
 В следующей таблице показано, как предложение "это образец текста." совместно используется двумя перекрывающимися закладками.  
  
|Закладка|Text|  
|--------------|----------|  
|Перекрывающиеся закладки|[это {образец] текста.}|  
|Bookmark1|это образец|  
|Bookmark2|образец текста.|  
  
 Если назначить новый текст "это замена" закладке Bookmark1, то закладки больше не будут перекрываться, и в закладке Bookmark2 останется только текст, который не был изначально частью Bookmark1.  
  
|Закладка|Text|  
|--------------|----------|  
|Две отдельные закладки|[это замена]{ текста}|  
|Bookmark1|это замена|  
|Bookmark2|текста.|  
  
 Если одна закладка полностью содержится в другой закладке и текст внешней закладки изменяется, внутренняя закладка не удаляется. Однако внутренняя закладка становится пустой и перемещается в конец внешней закладки. В следующей таблице показано, как предложение "это образец текста." используется совместно с закладкой, содержащейся в другой закладке.  
  
|Закладка|Text|  
|--------------|----------|  
|Перекрывающиеся закладки|[это {образец} текста.]|  
|Bookmark1|это образец текста.|  
|Bookmark2|пример|  
  
 Если назначить новый текст "это замена" закладке Bookmark1, то закладки больше не будут перекрываться, и закладка Bookmark2 становится пустой закладкой, расположенной в конце Bookmark1.  
  
|Закладка|Text|  
|--------------|----------|  
|Две отдельные закладки|[это замена.]{}|  
|Bookmark1|это замена.|  
|Bookmark2|*\<пустой >*|  
  
## <a name="events"></a>События  
 Для элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> доступны следующие события:  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>  
  
## <a name="see-also"></a>См. также  
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Пошаговое руководство: Создание контекстного меню для закладок](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  