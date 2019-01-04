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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f19bf36b145a5f2c1b4e841a96cdd485a0fb6ac1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53946708"
---
# <a name="xmlmappedrange-control"></a>Элемент управления XmlMappedRange
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Управления представляет собой диапазон, который создается только в том случае, когда неповторяющийся элемент схемы сопоставляется с ячейки в Microsoft Office Excel. Например, если `maxOccurs` атрибут элемента схемы имеет значение 1. После того как Visual Studio создаст в сопоставленном диапазоне XML, можно запрограммировать напрямую, не обращаясь к объектной модели Excel. Можно удалить только <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемента управления в Excel при удалении сопоставления элементов.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Использовать сопоставление XML в Excel? ](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## <a name="bind-data-to-the-control"></a>Привязка данных к элементу управления  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Элемент управления поддерживает привязку одного поля данных (простая привязка данных). <xref:Microsoft.Office.Tools.Excel.ListObject> Управления сложной привязкой данных и создается автоматически при сопоставлении повторяющегося элемента схемы ячейке. Дополнительные сведения см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Управления привязан к источнику данных с помощью <xref:System.Windows.Forms.Control.DataBindings%2A> свойство. Когда <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> добавляется в ячейку листа, Visual Studio автоматически создает набор данных на основе данных в этих ячейках и привязывает элемент управления для этого набора данных. Свойство привязки данных по умолчанию <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> является <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Если данные в привязанном наборе обновляются посредством какого-либо механизма, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управления отражает изменения.  
  
## <a name="formatting"></a>Форматирование  
 Можно применить одинаковое форматирование к <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> элемент управления, который можно применить к <xref:Microsoft.Office.Interop.Excel.Range>. Это включает границы, шрифты, формат чисел и стили.  
  
## <a name="events"></a>События  
 События, доступные для <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управления:  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>См. также  
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Практическое руководство. Добавление элементов управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Практическое руководство. Сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
