---
title: решения Excel
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 532689afe4e07c3151be6eac923f2b591aa34f46
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253624"
---
# <a name="excel-solutions"></a>решения Excel
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания настроек на уровне документа и надстроек VSTO для Microsoft Office Excel. Эти решения можно использовать для автоматизации Excel, расширения функциональных возможностей Excel и настройки пользовательского интерфейса Excel. Дополнительные сведения о различиях между настройками уровня документа и надстройками VSTO см. в разделе [Общие сведения о &#40;разработке решений Office&#41;VSTO](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 В данном разделе содержатся следующие сведения:

- [Автоматизируйте](#automating)работу с Excel.

- [Разработка настроек на уровне документа для Excel](#doclevel).

- [Разработка надстроек VSTO для Excel](#applevel).

- [Настройка пользовательского интерфейса Excel](#UI).

## <a name="automating"></a>Автоматизация Excel
 Объектная модель Excel предоставляет различные типы, которые можно использовать для автоматизации Excel. Например, можно программно создавать диаграммы, форматировать листы и задавать значения диапазонов и ячеек. Дополнительные сведения см. в разделе [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md).

 При разработке своих решений Excel в Visual Studio можно также использовать *ведущие элементы* и *элементы управления ведущего приложения* . Данные элементы являются объектами, которые расширяют некоторые часто используемые объекты в объектной модели Excel, например объекты <xref:Microsoft.Office.Interop.Excel.Worksheet> и <xref:Microsoft.Office.Interop.Excel.Range> . Расширенные объекты ведут себя как объекты Excel, на которых они основаны, но добавляют объектам дополнительные события и возможности по привязке данных. Дополнительные сведения см. в разделе [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md).

## <a name="doclevel"></a>Разработка настроек на уровне документа для Excel
 Настройка на уровне документа для Microsoft Office Excel состоит из сборки, связанной с конкретной книгой. Как правило, сборка расширяет книгу посредством настройки пользовательского интерфейса и автоматизации Excel. В отличие от надстройки VSTO, которая связана с самим приложением Excel, функциональные возможности, реализуемые в настройке, доступны только в том случае, когда соответствующая книга открыта в Excel.

 Чтобы создать проект настройки на уровне документа для Excel, используйте шаблоны проектов книги Excel или шаблона Excel в диалоговом окне **Новый проект** Visual Studio. Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Дополнительные сведения о работе настроек уровня документа см. в разделе [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).

### <a name="excel-customization-programming-model"></a>Модель программирования настройки Excel
 При создании проекта на уровне документа для Excel Visual Studio создает несколько классов, которые служат базой для вашего решения: `ThisWorkbook`, `Sheet1`, `Sheet2`и `Sheet3`. Эти классы представляют книгу и листы, связанные с решением, а также отправную точку для написания кода.

 Дополнительные сведения о созданных классах и других функциях, которые можно использовать в проекте уровня документа, см. в разделе [Program настроек на уровне документа](../vsto/programming-document-level-customizations.md).

## <a name="applevel"></a>Разработка надстроек VSTO для Excel
 Надстройка VSTO для Microsoft Office Excel состоит из сборки, загружаемой в Excel. Как правило, сборка расширяет Excel посредством настройки пользовательского интерфейса и автоматизации Excel. В отличие от настройки на уровне документа, связанной с определенной книгой, функциональные возможности, реализуемые в надстройке VSTO, не ограничиваются ни одной книгой.

 Чтобы создать проект надстройки VSTO для Excel, используйте шаблоны проектов книги Excel или шаблона Excel в диалоговом окне **Новый проект** Visual Studio. Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Общие сведения о работе надстроек VSTO см. в разделе [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Модель программирования надстроек Excel
 При создании проекта надстройки VSTO Excel Visual Studio создает класс с именем `ThisAddIn`, который служит базой для вашего решения. Этот класс представляет отправную точку для написания собственного кода, а также предоставляет объектную модель Excel для надстройки VSTO.

 Дополнительные сведения о `ThisAddIn` классе и других функциях Visual Studio, которые можно использовать в надстройке VSTO, см. в разделе [программирование VSTO-надстроек](../vsto/programming-vsto-add-ins.md).

## <a name="UI"></a>Настройка пользовательского интерфейса Excel
 Для настройки пользовательского интерфейса Excel можно использовать несколько способов. Некоторые параметры доступны для всех типов проектов. Также есть параметры, доступные только для надстроек VSTO или настроек на уровне документа.

### <a name="options-for-all-project-types"></a>Параметры для всех типов проектов
 В следующей таблице перечислены параметры настройки, доступные для настроек на уровне документа и надстроек VSTO.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Настройка ленты.|[Общие сведения о ленте](../vsto/ribbon-overview.md)|
|Добавление элементов управления Windows Forms или расширенных элементов управления Excel на лист в настраиваемой книге для настройки на уровне документа или в любой открытый документ для надстройки VSTO.|[Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Практическое руководство. Добавление элементов управления диаграммы на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Практическое руководство. Добавление элементов управления NamedRange в листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Параметры для настроек уровня документа
 В следующей таблице перечислены параметры настройки, доступные только для настроек на уровне документа.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Добавление панели действий в книгу.|[Обзор панели действий](../vsto/actions-pane-overview.md)<br /><br /> [Практическое руководство. Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Добавление расширенных элементов управления диапазоном, сопоставленных с XML-узлами, на лист.|[Практическое руководство. Добавление элементов управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>Параметры для надстроек VSTO
 В следующей таблице перечислены параметры настройки, доступные только для надстроек VSTO.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Создание настраиваемой области задач.|[Настраиваемые области задач](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>См. также

| Заголовок | Описание |
| - | - |
| [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md) | Содержит общие сведения об основных типах, предоставляемых объектной моделью Excel. |
| [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md) | Содержит сведения о расширенных объектах (предоставляемых из [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), которые можно использовать в решениях Excel. |
| [Глобализация и локализация решений Excel](../vsto/globalization-and-localization-of-excel-solutions.md) | Содержит сведения об особенностях решений Excel, которые будут выполняться на компьютерах с локализованными настройками для Windows. |
| [Общие сведения об элементах управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md) | Содержит сведения о добавлении элементов управления Windows Forms на листы Excel. |
| [Пошаговое руководство: Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Содержит сведения о создании базовой настройки на уровне документа для Excel. |
| [Пошаговое руководство: Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Содержит сведения о создании базовой надстройки VSTO для Excel. |
| [Пошаговое руководство: Добавление элементов управления на лист во время выполнения в проекте надстройки VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Содержит сведения о добавлении кнопки Windows Forms, <xref:Microsoft.Office.Tools.Excel.NamedRange>, и <xref:Microsoft.Office.Tools.Excel.ListObject> на лист во время выполнения с помощью надстройки VSTO. |
| [Общие сведения о совместном редактировании и надстройках](./understanding-coauthoring-and-addins.md) | Описывает корректировки, которые могут потребоваться в решениях для совместной разработки. |
| [Excel 2010 в разработке решений для Office](http://go.microsoft.com/fwlink/?LinkId=199011) | Ссылки на статьи и справочную документацию о разработке решений Excel. Они не относятся к разработке решений Office в Visual Studio. |
