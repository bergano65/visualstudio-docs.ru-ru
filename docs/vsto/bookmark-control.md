---
title: Bookmark - элемент управления
description: Сведения о том, как элемент управления Bookmark представляет собой закладку с уникальным именем, предоставляет события и может быть привязан к данным.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1da30943eff228aad3c5413c5d8faea337634e9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905260"
---
# <a name="bookmark-control"></a>Bookmark - элемент управления
  Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> представляет собой закладку с уникальным именем, которая предоставляет события и может быть привязана к данным. Закладка может использоваться как заполнитель для пометки элемента или расположения в документе Microsoft Office Word. Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> представляет собой комбинацию объектов <xref:Microsoft.Office.Interop.Word.Bookmark> и <xref:Microsoft.Office.Interop.Word.Range> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 В проектах на уровне документа вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документ во время разработки или во время выполнения. В проектах надстроек VSTO вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в любой открытый документ во время выполнения. Дополнительные сведения см. [в разделе руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

## <a name="bind-data-to-the-control"></a>Привязка данных к элементу управления
 Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> поддерживает простую привязку данных. Закладка должна быть привязана к источнику данных с помощью свойства <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . Свойство <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> — это свойство привязки данных по умолчанию для закладки.

 Если данные в связанном наборе данных обновляются, эти <xref:Microsoft.Office.Tools.Word.Bookmark> изменения отображаются в элементе управления.

 В проектах на уровне документа вы также можете привязывать данные к закладкам с помощью окна **Источники данных** . Дополнительные сведения см. [в разделе инструкции. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Форматирование
 Любое форматирование, которое можно применить к <xref:Microsoft.Office.Interop.Word.Bookmark> , также можно применить и к элементу управления <xref:Microsoft.Office.Tools.Word.Bookmark> . Это форматирование включает в себя шрифты, отступы, промежутки, нумерацию и стили.

## <a name="assign-text-to-the-bookmark"></a>Назначение текста закладке
 Дополнительное различие между объектом <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> и элементом управления <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> состоит в их поведении при назначении текста закладке. Если вы назначаете текст <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>нулевой длины, этот текст добавляется справа от закладки, а закладка останется нулевой длины. Однако если вы назначаете текст <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>нулевой длины, этот текст вставляется в закладку, и длина закладки увеличивается на число вставленных символов.

 Элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> также имеет свойство <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> . Это свойство отличается от <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> свойства, доступного в <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> свойстве <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> элемента управления, или <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> свойства <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> объекта.

|Свойство Text|Описание|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Используйте это свойство для отображения текста в закладке и оставления закладки в документе. Назначение текста закладке расширяет диапазон закладки и не удаляет ее.<br /><br /> Например, `Bookmark1.Text = "Hello world"` вставляет текст в закладку и оставляет закладку неизменной.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Используйте это свойство для отображения текста в расположении закладки и автоматического удаления ее. Например, `Bookmark1.Range.Text = "Hello world"` вставляет текст в закладку и удаляет закладку.|

## <a name="rename-the-control-at-design-time"></a>Переименование элемента управления во время разработки
 В проектах уровня документа при перетаскивании элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> из **панели элементов** в документ Visual Studio автоматически создает имя для этого элемента управления. Вы можете изменить это имя в окне **Свойства** .

## <a name="overlapping-controls"></a>Перекрывающиеся элементы управления
 Элементы управления Bookmark могут перекрывать друг друга. Один и тот же текст может совместно использоваться несколькими закладками. При назначении нового текста одной из перекрывающихся закладок он содержит только новый текст, а закладки больше не перекрываются. Теперь другая закладка содержит только текст, который не был совместно использоваться исходными перекрывающимися закладками.

 В следующей таблице показано, как предложение "это образец текста." совместно используется двумя перекрывающимися закладками:

|Закладка|Текст|
|--------------|----------|
|Перекрывающиеся закладки|[это {образец] текста.}|
|Bookmark1|это образец|
|Bookmark2|образец текста.|

 Если назначить новый текст "это замена" для Bookmark1 закладки не перекрываются, и Bookmark2 оставляет только текст, который изначально не был частью Bookmark1.

|Закладка|Текст|
|--------------|----------|
|Две отдельные закладки|[это замена]{ текста}|
|Bookmark1|это замена|
|Bookmark2|текста.|

При изменении текста закладки, содержащей другую закладку, внутренняя закладка не удаляется. Однако внутренняя закладка превращается в пустую закладку и перемещается в конец внешней закладки.

В следующей таблице показано, как предложение "это образец текста." совместно используется закладкой, которая содержится в другой закладке:

|Закладка|Текст|
|--------------|----------|
|Перекрывающиеся закладки|[это {образец} текста.]|
|Bookmark1|это образец текста.|
|Bookmark2|sample|

 Если назначить новый текст "это замена" закладке Bookmark1, то закладки больше не будут перекрываться, и закладка Bookmark2 становится пустой закладкой, расположенной в конце Bookmark1.

|Закладка|Текст|
|--------------|----------|
|Две отдельные закладки|[это замена.]{}|
|Bookmark1|это замена.|
|Bookmark2|*\<empty>*|

## <a name="events"></a>События

Для элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> доступны следующие события:

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

- <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>См. также раздел

- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Пошаговое руководство. создание контекстных меню для закладок](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)