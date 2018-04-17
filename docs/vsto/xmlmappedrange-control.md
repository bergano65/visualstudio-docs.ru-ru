---
title: Элемент управления XmlMappedRange | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 1bc4516f0ca14427e5e63a40ae58ddd60436dfd6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="xmlmappedrange-control"></a>Элемент управления XmlMappedRange
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Элемент управления является диапазон, который создается только при сопоставлении неповторяющегося элемента схемы ячейке в Microsoft Office Excel. Например, если `maxOccurs` атрибут элемента схемы равен 1. Когда Visual Studio создаст сопоставленный диапазон XML, можно программировать непосредственно, не обращаясь к объектной модели Excel. Можно удалить только <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управления в Excel при удалении сопоставления элементов.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как сделать I: использования сопоставления XML в Excel?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## <a name="binding-data-to-the-control"></a>Привязка данных к элементу управления  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Элемент управления поддерживает привязку одного поля данных (простая привязка данных). <xref:Microsoft.Office.Tools.Excel.ListObject> Может управления поддерживает сложную привязку данных и создается автоматически при сопоставлении повторяющегося элемента схемы ячейке. Для получения дополнительной информации см. [ListObject Control](../vsto/listobject-control.md).  
  
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Управления привязаны к источнику данных с помощью <xref:System.Windows.Forms.Control.DataBindings%2A> свойство. Когда <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> добавляется в ячейку листа, Visual Studio автоматически создает набор данных на основе данных в этих ячейках и привязывает элемент управления в указанный набор данных. Свойство привязки данных по умолчанию <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> — <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Если данные в привязанном наборе обновляются посредством какого-либо механизма <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управления отражает изменения.  
  
## <a name="formatting"></a>Форматирование  
 Можно применить то же форматирование к <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управления, можно применить к <xref:Microsoft.Office.Interop.Excel.Range>. Это включает границы, шрифты, формат чисел и стили.  
  
## <a name="events"></a>События  
 Доступные для события <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> управления являются:  
  
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
 [Как: Добавление элементов управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Как: сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  