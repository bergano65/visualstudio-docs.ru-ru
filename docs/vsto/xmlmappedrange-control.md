---
title: "Элемент управления XmlMappedRange | Microsoft Docs"
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
  - "XMLMappedRange - элемент управления"
  - "XMLMappedRange - элемент управления, привязка данных"
  - "XMLMappedRange - элемент управления, события"
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Элемент управления XmlMappedRange
  Элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> является диапазоном, который создается только при сопоставлении неповторяющегося элемента схемы ячейке в документе Microsoft Office Excel.  Например, если атрибут `maxOccurs` элемента схемы имеет значение 1.  Созданный в Visual Studio сопоставленный диапазон XML можно программировать непосредственно, не обращаясь к объектной модели Excel.  Элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> в Excel можно удалить, только когда удалено сопоставление элементов.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![ссылка на видео](../vsto/media/playvideo.png "ссылка на видео") Для просмотра связанных демонстрационных видеороликов перейдите по ссылке [How Do I: Use XML Mapping in Excel?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## Привязка данных к элементу управления  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> поддерживает привязку только к одному полю данных \(простая привязка данных\).  Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> может поддерживать сложную привязку данных и создается автоматически при сопоставлении повторяющегося элемента схемы ячейке.  Дополнительные сведения см. в разделе [Элемент управления ListObject](../vsto/listobject-control.md).  
  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> привязывается к источнику данных с помощью свойства <xref:System.Windows.Forms.Control.DataBindings%2A>.  Когда в ячейку листа добавляется <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, Visual Studio автоматически создает из данных в сопоставленных ячейках набор данных и привязывает к нему элемент управления.  Для <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> по умолчанию используется свойство привязки данных <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Если данные в привязанном наборе обновляются каким\-либо способом, изменения отображаются в элементе управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>.  
  
## Форматирование  
 Для элемента управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> можно применить то же форматирование, что и для <xref:Microsoft.Office.Interop.Excel.Range>.  Это относится к границам, шрифтам, числовому формату и стилям.  
  
## События  
 Ниже перечислены события, доступные для элемента управления <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>.  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## См. также  
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Практическое руководство. Добавление элементов управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Практическое руководство. Сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  