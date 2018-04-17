---
title: 'Как: изменение размеров элементов управления ListObject | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 12a81e6bb4a0484b79ad42b8fbab77db97ea82c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-listobject-controls"></a>Практическое руководство. Изменение размера элементов управления ListObject
  Размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> задается при добавлении его в книгу Microsoft Office Excel; однако позднее может потребоваться изменить его размер. Например, в список из двух столбцов может потребоваться добавить третий столбец.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В проектах уровня документа вы можете изменять размер элементов управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время разработки или во время выполнения. В проекте надстройки VSTO вы можете изменять размер элементов управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время выполнения.  
  
 В этом разделе описываются следующие задачи.  
  
-   [Изменение размеров элементов управления ListObject во время разработки](#designtime)  
  
-   [Изменение размеров элементов управления ListObject во время выполнения в проекте уровня документа](#runtimedoclevel)  
  
-   [Изменение размеров элементов управления ListObject во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
 Дополнительные сведения об элементах управления <xref:Microsoft.Office.Tools.Excel.ListObject> см. в разделе [ListObject Control](../vsto/listobject-control.md).  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как добавление столбцов в объект списка с привязкой к данным во время выполнения?](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Изменение размеров элемента управления ListObject во время разработки  
 Чтобы изменить размер списка, можно щелкнуть и перетащить один из маркеров размера или переопределить его размер в диалоговом окне **изменения размеров списка** .  
  
#### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Изменение размеров списка в диалоговом окне изменения размера списка  
  
  
1.  Щелкните в любом месте <xref:Microsoft.Office.Tools.Excel.ListObject> таблицы. **Работа с таблицами, конструктор** появляется вкладка на ленте.  
  
2.  В разделе «Свойства» щелкните **изменить размер таблицы**.  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  Выберите новый диапазон данных для таблицы.  
  
4.  Нажмите кнопку **ОК**.  
  
##  <a name="runtimedoclevel"></a> Изменение размеров элемента управления ListObject во время выполнения в проекте уровня документа  
 Вы можете изменить размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время выполнения с помощью метода <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Этот метод нельзя использовать для перемещения элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> на новое место в листе. Заголовки должны оставаться в той же строке, а измененный элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> должен совмещаться с первоначальным объектом-списком. Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с измененным размером должен содержать строку заголовка и хотя бы одну строку данных.  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Изменение размеров объекта-списка программными средствами  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который охватывает ячейки от **A1** до **В3** в `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Изменение размеров ListObject во время выполнения в проекте надстройки VSTO  
 Вы можете изменить размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> в любом открытом листе во время выполнения. Дополнительные сведения о добавлении элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> в лист с помощью надстройки VSTO см. в разделе [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### <a name="to-resize-a-list-object-programmatically"></a>Изменение размеров объекта-списка программными средствами  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который охватывает ячейки от **A1** до **В3** в `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)   
 [Как: Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Как: изменение размеров элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Практическое руководство. Изменение размеров элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)  
  
  