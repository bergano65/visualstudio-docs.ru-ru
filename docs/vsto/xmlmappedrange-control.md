---
title: Элемент управления XmlMappedRange
description: Узнайте, что элемент управления XmlMappedRange — это диапазон, который создается только в том случае, если неповторяющийся элемент схемы сопоставляется с ячейкой в Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2849b815c38555be6b149544bb9d9953fe85ec4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894404"
---
# <a name="xmlmappedrange-control"></a>Элемент управления XmlMappedRange
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Элемент управления — это диапазон, который создается только в том случае, если неповторяющийся элемент схемы сопоставляется с ячейкой в Microsoft Office Excel. Например, если `maxOccurs` атрибут элемента Schema равен 1. После того как Visual Studio создаст сопоставленный диапазон XML, вы можете программировать его напрямую, не обращаясь к объектной модели Excel. <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Элемент управления в Excel можно удалить только при удалении сопоставления элементов.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Привязка данных к элементу управления
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Элемент управления поддерживает привязку к одному полю данных (простая привязка данных). <xref:Microsoft.Office.Tools.Excel.ListObject>Элемент управления может поддерживать сложную привязку данных и автоматически создаваться при сопоставлении повторяющегося элемента схемы с ячейкой. Дополнительные сведения см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Элемент управления привязан к источнику данных с помощью <xref:System.Windows.Forms.Control.DataBindings%2A> Свойства. При <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> добавлении объекта в ячейку листа Visual Studio автоматически создает набор данных на основе данных в сопоставленных ячейках и привязывает элемент управления к этому набору данных. Свойство привязки данных по умолчанию для <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> имеет значение <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> .

 Если данные в связанном наборе данных обновляются с помощью любого механизма, этот <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемент управления отражает изменения.

## <a name="formatting"></a>Форматирование
 Вы можете применить то же форматирование к <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элементу управления, который можно применить к <xref:Microsoft.Office.Interop.Excel.Range> . Это включает границы, шрифты, формат чисел и стили.

## <a name="events"></a>События
 Для <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемента управления доступны следующие события:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>См. также раздел
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Как добавить элементы управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Как сопоставлять схемы с листами в Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
