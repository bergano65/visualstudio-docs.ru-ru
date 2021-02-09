---
title: Автоматизация Excel с помощью расширенных объектов
description: Узнайте, что при разработке решений Excel в Visual Studio можно использовать ведущие элементы и элементы управления ведущего приложения в решениях.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e20251d695f36940fec3831d3fa78fd995a058e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882496"
---
# <a name="automate-excel-by-using-extended-objects"></a>Автоматизация Excel с помощью расширенных объектов
  При разработке своих решений Excel в Visual Studio можно также использовать *ведущие элементы* и *элементы управления ведущего приложения*. Это объекты, которые расширяют некоторые часто используемые объекты в объектной модели Excel (т. е. объектной модели, которая предоставляется основной сборкой взаимодействия для Excel), такие как объекты <xref:Microsoft.Office.Interop.Excel.Worksheet> и <xref:Microsoft.Office.Interop.Excel.Range> . Расширенные объекты ведут себя как объекты Excel, на которых они основаны, но добавляют объектам дополнительные события и возможности по привязке данных.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Ведущие элементы и элементы управления ведущего приложения доступны в надстройке VSTO и настройке на уровне документа, хотя контекст, в котором они используются, отличается для каждого типа решения. Дополнительные сведения см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

## <a name="excel-host-items"></a>Ведущие элементы Excel
 Проекты Excel предоставляют доступ к нескольким ведущим элементам:

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. Этот ведущий элемент содержит и представляет лист в проекте. Также он служит контейнером для управляемых элементов управления, в том числе элементов управления ведущего приложения и элементов управления Windows Forms, и хранит сведения об элементах управления на его поверхности. Дополнительные сведения см. в разделе [ведущий элемент листа](../vsto/worksheet-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.Workbook>. Этот ведущий элемент представляет книгу в проекте и выступает в роли контейнера для компонентов, общих для всех листов в книге. Дополнительные сведения см. в разделе [ведущий элемент книги](../vsto/workbook-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Этот ведущий элемент на листе Excel содержит только диаграмму и предоставляет события.

     При добавлении листа диаграммы во время разработки в качестве нового листа в проект настройки уровня документа Microsoft Office Excel Visual Studio автоматически создает ведущий элемент <xref:Microsoft.Office.Tools.Excel.ChartSheet> .

     Хотя ведущий элемент <xref:Microsoft.Office.Tools.Excel.ChartSheet> — это лист Excel, невозможно добавить какие-либо элементы управления на лист с диаграммой. Если вы хотите использовать другие элементы управления на листе с диаграммой, не используйте лист диаграммы. Вместо этого можно поместить диаграмму как внедренный объект на лист с помощью элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.Chart> . Дополнительные сведения см. в разделе [элемент управления диаграммы](../vsto/chart-control.md).

## <a name="excel-host-controls"></a>элементы управления ведущего приложения Excel
 Существует несколько элементов управления ведущего приложения для Excel, которые помогают создавать, организовывать и автоматизировать книги и листы. Они предоставляют события и возможности привязки к данным, не поддерживаемые их аналогами в управляемой объектной модели Excel.

 Дополнительные сведения о ведущих элементах управления, которые можно использовать в проектах Excel, см. в следующих разделах:

- [Элемент управления диаграммы](../vsto/chart-control.md)

- [Элемент управления ListObject](../vsto/listobject-control.md)

- [Элемент управления NamedRange](../vsto/namedrange-control.md)

- [Элемент управления XmlMappedRange](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>См. также раздел
- [Как заполнить элементы управления ListObject данными](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Как добавлять элементы управления "Диаграмма" на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Как добавить элементы управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Как добавить элементы управления NamedRange в листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Как добавить элементы управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Как изменить размер элементов управления NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Как изменить размер элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Как проверить данные при добавлении новой строки в элемент управления ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Как сопоставлять столбцы ListObject с данными](../vsto/how-to-map-listobject-columns-to-data.md)
- [Пошаговое руководство. Программирование событий элемента управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
