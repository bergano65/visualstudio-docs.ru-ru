---
title: Практическое руководство. Изменение размера элементов управления ListObject
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6d996cfcfb9dd8c63cf31b203905b486b3a1c82
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598470"
---
# <a name="how-to-resize-listobject-controls"></a>Практическое руководство. Изменение размера элементов управления ListObject
  Размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> задается при добавлении его в книгу Microsoft Office Excel; однако позднее может потребоваться изменить его размер. Например, в список из двух столбцов может потребоваться добавить третий столбец.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Вы можете изменить размер <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления во время разработки или во время выполнения в проектах уровня документа. Вы можете изменить размер <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления во время выполнения в проекте надстройки VSTO.

 В этом разделе описываются следующие задачи.

- [Изменение размера элементов управления ListObject во время разработки](#designtime)

- [Изменение размера элементов управления ListObject во время выполнения в проекте уровня документа](#runtimedoclevel)

- [Изменение размера элементов управления ListObject во время выполнения в проекте надстройки VSTO](#runtimeaddin)

  Дополнительные сведения о <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления, см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

  ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Добавление столбцов в объект списка с привязкой к данным во время выполнения? ](http://go.microsoft.com/fwlink/?LinkID=130318).

##  <a name="designtime"></a> Изменение размера элемента управления ListObject во время разработки
 Чтобы изменить размер списка, можно щелкнуть и перетащить один из маркеров размера или переопределить его размер в диалоговом окне **изменения размеров списка** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Изменение размеров списка в диалоговом окне изменения размера списка


1.  Щелкните в любом месте <xref:Microsoft.Office.Tools.Excel.ListObject> таблицы. **Средства таблиц** > **разработки** появится вкладка на ленте.

2.  В разделе "Свойства", щелкните **изменение размера таблицы**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3.  Выберите новый диапазон данных для таблицы.

4.  Нажмите кнопку **ОК**.

##  <a name="runtimedoclevel"></a> Изменение размеров элемента управления ListObject во время выполнения в проекте уровня документа
 Вы можете изменить размер <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления во время выполнения с помощью <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> метод. Этот метод нельзя использовать для перемещения элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> на новое место в листе. Заголовки должны оставаться в той же строке, а измененный элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> должен совмещаться с первоначальным объектом-списком. Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с измененным размером должен содержать строку заголовка и хотя бы одну строку данных.

### <a name="to-resize-a-list-object-programmatically"></a>Изменение размеров объекта-списка программными средствами

1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который охватывает ячейки от **A1** до **В3** в `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2.  Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

##  <a name="runtimeaddin"></a> Изменение размеров ListObject во время выполнения в проекте надстройки VSTO
 Вы можете изменить размер <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления в любой открытый лист во время выполнения. Дополнительные сведения о добавлении <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления на лист с помощью надстройки VSTO, см. в разделе [как: Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Изменение размеров объекта-списка программными средствами

1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который охватывает ячейки от **A1** до **В3** в `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2.  Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>См. также
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
- [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Практическое руководство. Изменение размера элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Практическое руководство. Изменение размера элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)
