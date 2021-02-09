---
title: Как изменить размер элементов управления ListObject
description: Узнайте, как можно использовать Visual Studio для программного изменения размера элементов управления ListObject в книге Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e839e253e54e7c9c0358bef7330f9e330684b809
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927838"
---
# <a name="how-to-resize-listobject-controls"></a>Как изменить размер элементов управления ListObject
  Размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> задается при добавлении его в книгу Microsoft Office Excel; однако позднее может потребоваться изменить его размер. Например, в список из двух столбцов может потребоваться добавить третий столбец.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В проектах уровня документа вы можете изменять размер элементов управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время разработки или во время выполнения. Вы можете изменить размер <xref:Microsoft.Office.Tools.Excel.ListObject> элементов управления во время выполнения в проекте надстройки VSTO.

 В этом разделе описываются следующие задачи.

- [Изменение размера элементов управления ListObject во время разработки](#designtime)

- [Изменение размера элементов управления ListObject во время выполнения в проекте уровня документа](#runtimedoclevel)

- [Изменение размера элементов управления ListObject во время выполнения в проекте надстройки VSTO](#runtimeaddin)

  Дополнительные сведения об элементах <xref:Microsoft.Office.Tools.Excel.ListObject> управления см. в разделе [элемент управления ListObject](../vsto/listobject-control.md).

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> Изменение размера элемента управления ListObject во время разработки
 Чтобы изменить размер списка, можно щелкнуть и перетащить один из маркеров размера или переопределить его размер в диалоговом окне **изменения размеров списка** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Изменение размеров списка в диалоговом окне изменения размера списка

1. Щелкните в любом месте  <xref:Microsoft.Office.Tools.Excel.ListObject> таблицы. Откроется вкладка Конструктор **инструментов таблиц**  >   на ленте.

2. В разделе Свойства щелкните **изменить размер таблицы**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Выберите новый диапазон данных для таблицы.

4. Нажмите кнопку **OK**.

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Изменение размера элемента управления ListObject во время выполнения в проекте уровня документа
 Вы можете изменить размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> во время выполнения с помощью метода <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Этот метод нельзя использовать для перемещения элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> на новое место в листе. Заголовки должны оставаться в той же строке, а измененный элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> должен совмещаться с первоначальным объектом-списком. Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с измененным размером должен содержать строку заголовка и хотя бы одну строку данных.

### <a name="to-resize-a-list-object-programmatically"></a>Изменение размеров объекта-списка программными средствами

1. Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который охватывает ячейки от **A1** до **В3** в `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Изменение размера элемента ListObject во время выполнения в проекте надстройки VSTO
 Размер элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> можно изменять во время выполнения на любом открытом листе. Дополнительные сведения о добавлении <xref:Microsoft.Office.Tools.Excel.ListObject> элемента управления на лист с помощью надстройки VSTO см. в разделе [как добавить элементы управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Изменение размеров объекта-списка программными средствами

1. Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> , который охватывает ячейки от **A1** до **В3** в `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Измените размер этого списка, чтобы он включал ячейки от **A1** до **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>См. также раздел
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Элемент управления ListObject](../vsto/listobject-control.md)
- [Как добавить элементы управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Как изменить размер элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Как изменить размер элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)
