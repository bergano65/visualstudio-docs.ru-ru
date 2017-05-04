---
title: "Практическое руководство. Изменение размера внутри ячеек листа Excel | Microsoft Docs"
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
  - "элементы управления [разработка решений Office в Visual Studio], изменение размеров"
  - "управляемые элементы управления, изменение размеров"
  - "Windows Forms - элементы управления [разработка решений Office в Visual Studio], изменение размеров"
  - "листы, изменение размеров"
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Практическое руководство. Изменение размера внутри ячеек листа Excel
  При изменении размеров столбцов или строк в листе любые размер элементов управления ведущего приложения, содержащиеся в ячейках, автоматически изменяется до высоты или ширины измененной ячейки.  Размер элементов управления Windows Forms по умолчанию не изменяется.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 При добавлении элементов управления во время разработки необходимо задать параметры расположения для каждого элемента.  
  
 При добавлении элемента управления Windows Forms программными средствами с указанием диапазона, размер элемента управления в ячейке автоматически изменяется в пределах указанного диапазона.  Дополнительные сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Изменение размеров элементов управления во время разработки  
  
#### Чтобы изменить размеры элементов управления во время разработки, необходимо выполнить следующие действия.  
  
1.  Перетащите элемент управления Windows Forms с **панели элементов** на лист.  
  
2.  Щелкните правой кнопкой мыши элемент управления и выберите пункт **Формат элемента управления**.  
  
3.  В диалоговом окне **Формат элемента управления** щелкните вкладку **Свойства**.  
  
4.  В области **Расположение объекта** выберите параметр **Перемещать и изменять размер с ячейкой**, а затем нажмите кнопку **ОК**.  
  
     После изменения размера ячейки, содержащей элемент управления, размер элемент будет изменен автоматически в соответствии с размером ячейки.  
  
## Изменение размеров элементов управления во время выполнения  
 При добавлении элемента управления Windows Forms во время выполнения с указанием диапазона <xref:Microsoft.Office.Interop.Excel.Range> в качестве расположения элемента, размер элемента управления автоматически изменяется при изменении ячейки, содержащей элемент.  
  
#### Чтобы изменить размеры элементов управления во время выполнения, необходимо выполнить следующие действия.  
  
1.  Добавить элемент управления в диапазон А1.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#5)]  
  
     После изменения размера ячейки, содержащей элемент управления, размер элемент будет изменен автоматически в соответствии с размером ячейки.  
  
## Сброс значений расположения элементов управления  
 Можно сбросить значения расположения и параметров изменения размеров элементов управления, присвоив свойству `Placement` одно из следующих значений <xref:Microsoft.Office.Interop.Excel.XlPlacement>:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### Чтобы элемент управления не изменял размер и не перемещался вместе с ячейкой, выполните следующие действия.  
  
1.  Вызовите свойство размещения элемента управления и присвойте ему значение <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#6)]  
  
## См. также  
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Практическое руководство. Скрытие элементов управления на листах при печати](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  