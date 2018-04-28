---
title: Bookmark-элемент управления | Документы Microsoft
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68934d202fbffc162b6888ab3a45cdf0b7fd439d
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2018
---
# <a name="bookmark-control"></a>Bookmark - элемент управления
  Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> представляет собой закладку с уникальным именем, которая предоставляет события и может быть привязана к данным. Закладка может использоваться как заполнитель для пометки элемента или расположения в документе Microsoft Office Word. Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> представляет собой комбинацию объектов <xref:Microsoft.Office.Interop.Word.Bookmark> и <xref:Microsoft.Office.Interop.Word.Range> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 В проектах на уровне документа вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документ во время разработки или во время выполнения. В проектах надстроек VSTO вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в любой открытый документ во время выполнения. Для получения дополнительной информации см. [Практическое руководство. Добавление закладок в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="binding-data-to-the-control"></a>Привязка данных к элементу управления
 Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> поддерживает простую привязку данных. Закладка должна быть привязана к источнику данных с помощью свойства <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . Свойство <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> — это свойство привязки данных по умолчанию для закладки.

 Если данные в привязанном наборе данных обновляются, <xref:Microsoft.Office.Tools.Word.Bookmark> управления показывает изменения.

 В проектах на уровне документа вы также можете привязывать данные к закладкам с помощью окна **Источники данных** . Для получения дополнительной информации см. [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Форматирование
 Любое форматирование, которое можно применить к <xref:Microsoft.Office.Interop.Word.Bookmark> , также можно применить и к элементу управления <xref:Microsoft.Office.Tools.Word.Bookmark> . Это форматирование включает шрифты, отступы, интервалы, нумерация и стили.

## <a name="assigning-text-to-the-bookmark"></a>Назначение текста закладке
 Дополнительное различие между <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> объекта и <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> управления состоит в их поведении при назначении текста закладке. Если вы назначаете текст нулевой длины <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>, этот текст добавляется справа от закладки, и закладка останется нулевой длины. Тем не менее если вы назначаете текст нулевой длины <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>, текст вставляется в закладку, и длина закладки увеличивается общее число вставленных символов.

 <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> Управления также имеет <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> свойства. Это свойство отличается от <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> свойство, доступное на <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> свойство <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> управления, или <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> свойство <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> объекта.

|Свойство Text|Описание|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Используйте это свойство для отображения текста в закладке и оставления закладки в документе. Назначение текста закладке расширяет диапазон закладки и не удаляет ее.<br /><br /> Например, `Bookmark1.Text = "Hello world"` вставляет текст в закладку и оставляет закладку неизменной.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Используйте это свойство для отображения текста в расположении закладки и автоматического удаления ее. Например, `Bookmark1.Range.Text = "Hello world"` вставляет текст в закладку и удаляет закладку.|

## <a name="renaming-the-control-at-design-time"></a>Переименование элемента управления во время разработки
 В проектах уровня документа при перетаскивании элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> из **панели элементов** в документ Visual Studio автоматически создает имя для этого элемента управления. Вы можете изменить это имя в окне **Свойства** .

## <a name="overlapping-controls"></a>Перекрывающиеся элементы управления
 Элементы управления Bookmark могут пересекаться друг с другом. Тот же текст может совместно использоваться несколькими закладками. При назначении нового текста одной из перекрывающихся закладок, она содержит только новый текст, и закладки больше не перекрывают друг друга. Другая закладка теперь содержит только текст, который не был совместно исходными перекрывающимися закладками.

 В следующей таблице показано, как предложение "это образец текста." совместно используется двумя перекрывающимися закладками:

|Закладка|Text|
|--------------|----------|
|Перекрывающиеся закладки|[это {образец] текста.}|
|Bookmark1|это образец|
|Bookmark2|образец текста.|

 Если назначить новый текст "это замена" закладке Bookmark1 то закладки не перекрываются, и закладка Bookmark2 только текст, который не был изначально частью Bookmark1.

|Закладка|Text|
|--------------|----------|
|Две отдельные закладки|[это замена]{ текста}|
|Bookmark1|это замена|
|Bookmark2|текста.|

Если изменить текст, содержащий другой закладке закладки, внутренняя закладка не удаляется. Однако внутренняя закладка становится пустой и перемещается в конец внешней закладки.

В следующей таблице показано, как предложение "это образец текста." совместно с закладкой, содержащейся в другой закладке:

|Закладка|Text|
|--------------|----------|
|Перекрывающиеся закладки|[это {образец} текста.]|
|Bookmark1|это образец текста.|
|Bookmark2|пример|

 Если назначить новый текст "это замена" закладке Bookmark1, то закладки больше не будут перекрываться, и закладка Bookmark2 становится пустой закладкой, расположенной в конце Bookmark1.

|Закладка|Text|
|--------------|----------|
|Две отдельные закладки|[Это замена.]{}|
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

- [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)
- [Практическое руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Пошаговое руководство. Создание контекстного меню для закладок](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)