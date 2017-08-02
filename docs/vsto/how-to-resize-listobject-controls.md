---
title: "Практическое руководство. Изменение размера элементов управления ListObject"
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
  - "элементы управления [разработка решений Office в Visual Studio], изменение размера"
  - "элемент управления ListObject, изменение размера"
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Практическое руководство. Изменение размера элементов управления ListObject
  Размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> задается при добавлении его в книгу Microsoft Office Excel; однако позднее может потребоваться изменить его размер. Например, в список из двух столбцов может потребоваться добавить третий столбец.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В проектах уровня документа вы можете изменять размер элементов управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время разработки или во время выполнения. В проекте надстройки VSTO вы можете изменять размер элементов управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время выполнения.  
  
 В этом разделе описываются следующие задачи.  
  
-   [Изменение размеров элементов управления ListObject во время разработки](#designtime)  
  
-   [Изменение размеров элементов управления ListObject во время выполнения в проекте уровня документа](#runtimedoclevel)  
  
-   [Изменение размеров элементов управления ListObject во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
 Дополнительные сведения об элементах управления <xref:Microsoft.Office.Tools.Excel.ListObject> см. в разделе [Элемент управления ListObject](../vsto/listobject-control.md).  
  
 ![ссылка на видео](~/docs/data-tools/media/playvideo.gif "ссылка на видео") Связанные демонстрационные видеоролики см. в разделе [Инструкции. Добавление столбцов в объект списка с привязкой к данным во время выполнения](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Изменение размеров элемента управления ListObject во время разработки  
 Чтобы изменить размер списка, можно щелкнуть и перетащить один из маркеров размера или переопределить его размер в диалоговом окне **изменения размеров списка**.  
  
#### Изменение размеров списка в диалоговом окне изменения размера списка  
  
1.  Щелкните правой кнопкой мыши элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
2.  Переведите указатель в элемент **Список**, а затем выберите пункт **Изменить размер списка** в контекстном меню.  
  
3.  Выделите ячейки, которые вы хотите использовать для определения размера списка.  
  
4.  Нажмите кнопку **ОК**.  
  
##  <a name="runtimedoclevel"></a> Изменение размеров элемента управления ListObject во время выполнения в проекте уровня документа  
 Вы можете изменить размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время выполнения с помощью метода <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A>. Этот метод нельзя использовать для перемещения элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> на новое место в листе. Заголовки должны оставаться в той же строке, а измененный элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> должен совмещаться с первоначальным объектом\-списком. Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с измененным размером должен содержать строку заголовка и хотя бы одну строку данных.  
  
#### Изменение размеров объекта\-списка программными средствами  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject>, который охватывает ячейки от **A1** до **В3** в `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#6)]  
  
2.  Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Изменение размеров ListObject во время выполнения в проекте надстройки VSTO  
 Вы можете изменить размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> в любом открытом листе во время выполнения. Дополнительные сведения о добавлении элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> в лист с помощью надстройки VSTO см. в разделе [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### Изменение размеров объекта\-списка программными средствами  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject>, который охватывает ячейки от **A1** до **В3** в `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#12)]  
  
2.  Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#13)]  
  
## См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)   
 [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Практическое руководство. Изменение размеров элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Практическое руководство. Изменения размера элементов управления "NamedRange"](../vsto/how-to-resize-namedrange-controls.md)  
  
  