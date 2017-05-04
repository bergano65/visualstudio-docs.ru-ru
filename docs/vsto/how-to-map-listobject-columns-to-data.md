---
title: "Практическое руководство. Сопоставление столбцов элемента управления ListObject данным | Microsoft Docs"
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
  - "данные [разработка решений Office в Visual Studio], сопоставление со столбцом ListObject"
  - "элемент управления ListObject, сопоставление данных"
ms.assetid: 2108d0c3-d595-410e-a0ae-3dd53bf6bcc7
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Практическое руководство. Сопоставление столбцов элемента управления ListObject данным
  При привязке элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> к <xref:System.Data.DataTable> вы можете не захотеть отображать все столбцы в списке или можете иметь некоторые столбцы, не привязанные к данным. Можно указать, какие столбцы должны отображаться в объекте <xref:Microsoft.Office.Tools.Excel.ListObject>, при вызове метода <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![ссылка на видео](../vsto/media/playvideo.png "ссылка на видео") Связанные демонстрационные видеоролики см. в разделе [Инструкции. Создание списка в Excel, подключенного к списку SharePoint](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## Сопоставление столбцов  
  
#### Сопоставление таблицы данных со столбцами в списке  
  
1.  Создайте <xref:System.Data.DataTable> на уровне класса.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#16)]  
  
2.  Добавьте примеры столбцов и данных в обработчик событий `Startup` класса `Sheet1` \(в проекте уровня документа\) или класса `ThisAddIn` \(в проекте надстройки VSTO\).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#17)]  
  
3.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> и передайте в него имена столбцов в порядке их отображения. Объект\-список будет привязан к вновь созданному объекту <xref:System.Data.DataTable>, но порядок столбцов в объекте\-списке будет отличаться от порядка их появления в <xref:System.Data.DataTable>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#18)]  
  
## Указание несопоставленных столбцов  
 При сопоставлении столбцов с <xref:System.Data.DataTable> можно также указать, что определенные столбцы не должны быть привязаны к данным, передав пустую строку. Затем новый столбец, не привязанный к данным, добавляется в элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
#### Указание несопоставленного столбца при сопоставлении столбцов ListObject  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> и передайте в него имена столбцов в порядке их отображения. Используйте пустую строку, чтобы указать, где добавляется несопоставленный столбец; в данном случае такой столбец добавляется между столбцом заголовка столбца и столбцом фамилии.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#19)]  
  
## Компиляция кода  
 В этом примере кода предполагается, что в листе, в котором этот код появляется, имеется существующий элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `list1`.  
  
## См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Практическое руководство. Заполнение данными элементов управления ListObject](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)  
  
  