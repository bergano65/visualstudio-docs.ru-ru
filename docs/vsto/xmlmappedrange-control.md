---
title: Элемент управления XmlMappedRange
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01417d9c08491edc882f7f758bb36e6184500e52
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985358"
---
# <a name="xmlmappedrange-control"></a>Элемент управления XmlMappedRange
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемент управления — это диапазон, который создается только в том случае, если неповторяющийся элемент схемы сопоставляется с ячейкой в Microsoft Office Excel. Например, если атрибут `maxOccurs` элемента схемы равен 1. После того как Visual Studio создаст сопоставленный диапазон XML, вы можете программировать его напрямую, не обращаясь к объектной модели Excel. Удалить элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> в Excel можно только при удалении сопоставления элементов.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Привязка данных к элементу управления
 Элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> поддерживает привязку к одному полю данных (простая привязка данных). Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> может поддерживать сложную привязку данных и автоматически создаваться при сопоставлении повторяющегося элемента схемы с ячейкой. Дополнительные сведения см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

 Элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> привязан к источнику данных с помощью свойства <xref:System.Windows.Forms.Control.DataBindings%2A>. При добавлении <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> в ячейку листа Visual Studio автоматически создает набор данных на основе данных в сопоставленных ячейках и привязывает элемент управления к этому набору данных. Свойство привязки данных <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> по умолчанию имеет значение <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.

 Если данные в связанном наборе данных обновляются с помощью любого механизма, то элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> отражает изменения.

## <a name="formatting"></a>Форматирование
 Вы можете применить то же форматирование к элементу управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, который можно применить к <xref:Microsoft.Office.Interop.Excel.Range>. Это включает границы, шрифты, формат чисел и стили.

## <a name="events"></a>события
 Для элемента управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> доступны следующие события:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>См. также
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Как добавить элементы управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Как сопоставлять схемы с листами в Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
