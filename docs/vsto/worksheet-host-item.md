---
title: Ведущий элемент листа
description: Сведения о том, что ведущий элемент листа является типом, расширяющим тип листа из основной сборки взаимодействия для Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host items [Office development in Visual Studio], Worksheet
- Excel [Office development in Visual Studio], worksheets
- Worksheet host items
- worksheets, events
- Worksheet host items, events
- Excel worksheets
- worksheets, Excel
- worksheets
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 12dc0823f1c7d1eb78867cb3529f955851f45b66
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955740"
---
# <a name="worksheet-host-item"></a>Ведущий элемент листа
  Ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> является типом, который расширяет тип <xref:Microsoft.Office.Interop.Excel.Worksheet> из основной сборки взаимодействия для Excel. Ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> предоставляет все свойства, методы и события объекта <xref:Microsoft.Office.Interop.Excel.Worksheet> , но также предоставляет дополнительные события и выступает в роли контейнера для элементов управления ведущего приложения и элементов управления Windows Forms.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В проектах уровня документа можно добавлять ведущие элементы <xref:Microsoft.Office.Tools.Excel.Worksheet> в проект во время разработки. В проектах надстройки VSTO во время выполнения можно создавать ведущие элементы <xref:Microsoft.Office.Tools.Excel.Worksheet> .

## <a name="understand-worksheet-host-items-in-document-level-projects"></a>Знакомство с ведущими элементами листа в проектах уровня документа
 При создании проекта уровня документа для Excel Visual Studio автоматически создает три ведущих элемента <xref:Microsoft.Office.Tools.Excel.Worksheet> в проекте. По умолчанию эти листы получают имена `Sheet1`, `Sheet2`и `Sheet3`. При создании проекта на основе существующей книги количество ведущих элементов зависит от числа листов в этой книге.

 Классы листов обеспечивают доступ к членам ведущего элемента <xref:Microsoft.Office.Tools.Excel.Worksheet> для выполнения основных задач в настройке, таких как изменение содержимого книги. Также можно использовать эти классы для добавления элементов управления в листы. Используя различные сочетания элементов управления и создавая код, можно привязать элементы управления к данным, собирать сведения от пользователя и реагировать на действия пользователя. Дополнительные сведения см. в разделе [Program настройки на уровне документа](../vsto/programming-document-level-customizations.md).

 Классы книги предоставляют место, в котором можно начать создание кода в проекте. Поскольку этот класс предоставляет все свойства, методы и события, что и объект <xref:Microsoft.Office.Interop.Excel.Worksheet> в основной сборке взаимодействия для Excel, вы также можете использовать эти классы для доступа к объектной модели Excel. Дополнительные сведения см. в разделе [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md).

 В проектах уровня документа вы можете добавлять дополнительные ведущие элементы <xref:Microsoft.Office.Tools.Excel.Worksheet> в проект во время разработки, добавив новый лист в книгу в конструкторе.

### <a name="rename-worksheets"></a>Переименование листов
 В проекте уровня документа можно переименовывать листы в конструкторе Visual Studio, но при этом меняется только отображаемое имя листа. Программным именем остается имя листа по умолчанию. При переименовании листа в окне **Свойства** изменяется только программное имя.

### <a name="limitations-of-the-worksheet-host-item-in-document-level-projects"></a>Ограничения ведущего элемента листа в проектах уровня документа
 В проектах уровня документа нельзя создавать ведущие элементы <xref:Microsoft.Office.Tools.Excel.Worksheet> во время выполнения. При создании нового листа Excel во время выполнения он будет иметь тип <xref:Microsoft.Office.Interop.Excel.Worksheet>. Поскольку это не ведущий элемент, он не может содержать никаких элементов управления ведущего приложения или элементов управления Windows Forms. Дополнительные сведения о создании документов во время выполнения см. [в разделе как программно добавлять новые листы в книги](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

## <a name="understand-worksheet-host-items-in-vsto-add-in-projects"></a>Знакомство с ведущими элементами листа в проектах надстроек VSTO
 В проектах уровня приложения можно создавать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> во время выполнения для любого листа, открытого в Excel. Вы можете использовать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> для добавления элементов управления в связанный лист или для обработки событий, которые недоступны в объектах <xref:Microsoft.Office.Interop.Excel.Worksheet> .

 Для создания ведущего элемента <xref:Microsoft.Office.Tools.Excel.Worksheet> используйте метод `GetVstoObject`. Дополнительные сведения см. [в разделе Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>См. также раздел
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Ведущий элемент книги](../vsto/workbook-host-item.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
