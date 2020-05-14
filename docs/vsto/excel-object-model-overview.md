---
title: Обзор модели Excel Object
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a823692a5cc0f154c514edff4fe9398de0efd212
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649416"
---
# <a name="excel-object-model-overview"></a>Обзор модели объектов Excel
  Для разработки решений, использующих Microsoft Office Excel, необходимо взаимодействие с объектами, предоставляемыми объектной моделью Excel. В этом разделе представлены наиболее важные объекты:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Объектная модель точно соответствует пользовательскому интерфейсу. Объект <xref:Microsoft.Office.Interop.Excel.Application> представляет приложение в целом, а каждый из объектов <xref:Microsoft.Office.Interop.Excel.Workbook> содержит коллекцию объектов `Worksheet`. Отсюда следует, что основная абстракция, представляющая ячейки, является объектом <xref:Microsoft.Office.Interop.Excel.Range>, позволяющим работать с отдельными ячейками или группой ячеек.

  В дополнение к модели объектов Excel проекты Office в Visual Studio предоставляют *элементы хоста* и *элементы управления,* расширяющие некоторые объекты в модели объектов Excel. Поведение ведущих элементов и элементов управления ведущего приложения аналогично поведению объектов Excel, однако они обладают дополнительными функциональными возможностями, такими как возможность привязки данных и дополнительные события. Для получения дополнительной информации [см. Автоматизировать Excel, используя расширенные объекты](../vsto/automating-excel-by-using-extended-objects.md) и [элементы host и обзор управления хостом.](../vsto/host-items-and-host-controls-overview.md)

  В этом разделе приводится краткий обзор объектной модели Excel. Для ресурсов, где вы можете узнать больше о всей модели объектов Excel, [см.](#ExcelOMDocumentation)

## <a name="access-objects-in-an-excel-project"></a>Доступ к объектам в проекте Excel
 При создании нового проекта VSTO Add-in для Excel Visual Studio автоматически создает *файл ThisAddIn.vb* или *ThisAddIn.cs* файл кода. Доступ к объекту приложения можно получить с помощью свойства `Me.Application` или `this.Application`.

 При создании нового проекта уровня документа для Excel можно создать новый проект книги Excel или шаблона Excel. Visual Studio автоматически создает в новом проекте Excel (как для проектов книги, так и для проектов шаблона) следующие файлы кода:

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sheet1.vb|Sheet1.cs|
|Sheet2.vb|Sheet2.cs|
|Sheet3.vb|Sheet3.cs|

 Класс `Globals` в проекте можно использовать для получения доступа к объекту `ThisWorkbook`, `Sheet1`, `Sheet2` или `Sheet3` вне соответствующего класса. Для получения дополнительной информации [см.](../vsto/global-access-to-objects-in-office-projects.md) Следующий пример <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> называет `Sheet1` метод независимо от того, находится `Sheet`ли код `ThisWorkbook` в одном из классов *n* или в классе.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Поскольку данные в документе Excel хорошо структурированы, объектная модель имеет прямую иерархическую структуру. Excel предоставляет сотни объектов, с которыми вы можете взаимодействовать, но вы можете получить хорошее начало на объектной модели, сосредоточив внимание на небольшой подмножество доступных объектов. К числу этих объектов относятся следующие четыре:

- Приложение

- Книга

- Лист

- Диапазон

  С этими четырьмя объектами и их составляющими связана большая часть работы в Excel.

### <a name="application-object"></a>Объект приложения
 Объект Excel <xref:Microsoft.Office.Interop.Excel.Application> представляет само приложение Excel. Объект <xref:Microsoft.Office.Interop.Excel.Application> представляет множество сведений о выполняемом приложении, параметрах соответствующего экземпляра и текущих объектах пользователя, открытых в экземпляре.

> [!NOTE]
> Не устанавливайте для свойства <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> объекта <xref:Microsoft.Office.Interop.Excel.Application> в Excel значение **false**. Установка значения false для этого свойства предотвращает инициирование событий в Excel, включая события элементов управления ведущего приложения.

### <a name="workbook-object"></a>Объект рабочей книги
 Объект <xref:Microsoft.Office.Interop.Excel.Workbook> представляет отдельную книгу в приложении Excel.

 Средства разработки Office в Visual Studio расширяют объект <xref:Microsoft.Office.Interop.Excel.Workbook> , предоставляя тип <xref:Microsoft.Office.Tools.Excel.Workbook> . Данный тип обеспечивает доступ ко всем функциям объекта <xref:Microsoft.Office.Interop.Excel.Workbook>. Для получения дополнительной информации смотрите [элемент хоста Workbook](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>Worksheet - объект
 Объект <xref:Microsoft.Office.Interop.Excel.Worksheet> является членом коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets>. Многие свойства, методы и события объекта <xref:Microsoft.Office.Interop.Excel.Worksheet> идентичны или похожи на элементы, предоставляемые объектами <xref:Microsoft.Office.Interop.Excel.Application> или <xref:Microsoft.Office.Interop.Excel.Workbook>.

 Excel предоставляет коллекцию <xref:Microsoft.Office.Interop.Excel.Sheets> как свойство объекта <xref:Microsoft.Office.Interop.Excel.Workbook>. Каждый член коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> является объектом <xref:Microsoft.Office.Interop.Excel.Worksheet> или <xref:Microsoft.Office.Interop.Excel.Chart>.

 Средства разработки Office в Visual Studio расширяют объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , предоставляя тип <xref:Microsoft.Office.Tools.Excel.Worksheet> . Этот тип предоставляет доступ ко всем возможностям объекта <xref:Microsoft.Office.Interop.Excel.Worksheet>, а также к новым возможностям, таким как возможность размещения управляемых элементов управления и обработки новых событий. Для получения дополнительной информации смотрите [элемент хоста листа](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>Range - объект
 Объект <xref:Microsoft.Office.Interop.Excel.Range> является объектом, который используется в приложениях Excel чаще всего. Для работы с какой-либо областью Excel ее необходимо указать в качестве объекта <xref:Microsoft.Office.Interop.Excel.Range>, а затем использовать методы и свойства этого диапазона. Объект <xref:Microsoft.Office.Interop.Excel.Range> может представлять ячейку, строку или столбец, выборку ячеек, содержащую один или несколько смежных или несмежных блоков ячеек, или даже группу ячеек, распределенную между разными листами.

 Visual Studio расширяет объект <xref:Microsoft.Office.Interop.Excel.Range>, предоставляя типы <xref:Microsoft.Office.Tools.Excel.NamedRange> и <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Эти типы обладают большинством функций объекта <xref:Microsoft.Office.Interop.Excel.Range>, а также новыми функциями, такими как возможность привязки данных и новые события. Для получения дополнительной информации [XmlMappedRange control](../vsto/xmlmappedrange-control.md) [см.](../vsto/namedrange-control.md)

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a>Используйте документацию модели объектов Excel
 Полные сведения об объектной модели Excel см. в справочнике по основной сборке взаимодействия (PIA) Excel и в справочнике по объектной модели VBA.

### <a name="primary-interop-assembly-reference"></a>Основная ссылка на интероп-сборку
 В справочной документации по основной сборке взаимодействия Excel описываются типы основной сборки взаимодействия для Excel. Эта документация доступна из следующего места: [Excel 2010 первичной interop сборки ссылки](office-primary-interop-assemblies.md).

 Для получения дополнительной информации о дизайне Excel PIA, таких как различия между классами и интерфейсами в PIA и как реализуются события в PIA, [см.](/previous-versions/office/office-12/ms247299(v=office.12))

### <a name="vba-object-model-reference"></a>Ссылка на модель объекта VBA
 В справочных документах по объектной модели VBA объектная модель Excel описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Для получения дополнительной [Excel 2010 object model reference](/office/vba/api/overview/Excel/object-model)информации см.

 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и участникам основной сборки взаимодействия Excel. Например, объект листа в ссылке модели модели <xref:Microsoft.Office.Interop.Excel.Worksheet> объекта VBA соответствует объекту в Excel PIA. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C#, если требуется использовать их в проекте Excel, создаваемом с помощью Visual Studio.

### <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[решения Excel](../vsto/excel-solutions.md)|Инструкции по созданию настроек уровня документа и надстроек VSTO для Microsoft Office Excel.|
|[Работа с диапазонами](../vsto/working-with-ranges.md)|Примеры выполнения стандартных задач с диапазонами.|
|[Работа с листами](../vsto/working-with-worksheets.md)|Примеры выполнения стандартных задач с листами.|
|[Работа с трудовыми книжеками](../vsto/working-with-workbooks.md)|Примеры выполнения стандартных задач с книгами.|
