---
title: "Общие сведения об объектной модели Excel | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: e4b2e46b-ea6c-4a88-a416-a7d4f495fc33
caps.latest.revision: "66"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b6bee3ed6bb88945d880f1fb855cec0f7cb9be27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="excel-object-model-overview"></a>Excel Object Model Overview
  Для разработки решений, использующих Microsoft Office Excel, необходимо взаимодействие с объектами, предоставляемыми объектной моделью Excel. В этом разделе представлены наиболее важные объекты:  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Объектная модель точно соответствует пользовательскому интерфейсу. Объект <xref:Microsoft.Office.Interop.Excel.Application> представляет приложение в целом, а каждый из объектов <xref:Microsoft.Office.Interop.Excel.Workbook> содержит коллекцию объектов `Worksheet`. Отсюда следует, что основная абстракция, представляющая ячейки, является объектом <xref:Microsoft.Office.Interop.Excel.Range>, позволяющим работать с отдельными ячейками или группой ячеек.  
  
 Помимо объектной модели Excel, проекты Office в Visual Studio предоставляют *ведущие элементы* и *элементы управления ведущего приложения* , расширяющие некоторые объекты из объектной модели Excel. Поведение ведущих элементов и элементов управления ведущего приложения аналогично поведению объектов Excel, однако они обладают дополнительными функциональными возможностями, такими как возможность привязки данных и дополнительные события. Дополнительные сведения см. в разделе [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md) и [ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md).  
  
 В этом разделе приводится краткий обзор объектной модели Excel. Ресурсы, где узнать больше о всей объектной модели Excel см. в разделе [использование документации по объектной модели Excel](#ExcelOMDocumentation).  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как следует использовать обработчики событий в Excel 2007 надстройки?](http://go.microsoft.com/fwlink/?LinkID=130291), и [как формы для создания пузырек Диаграммы в Excel? ](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## <a name="accessing-objects-in-an-excel-project"></a>Доступ к объектам в проекте Excel  
 При создании нового проекта надстройки VSTO для Excel среда Visual Studio автоматически создает файл кода ThisAddIn.vb или ThisAddIn.cs. Доступ к объекту приложения можно получить с помощью свойства `Me.Application` или `this.Application`.  
  
 При создании нового проекта уровня документа для Excel можно создать новый проект книги Excel или шаблона Excel. Visual Studio автоматически создает в новом проекте Excel (как для проектов книги, так и для проектов шаблона) следующие файлы кода:  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 Класс `Globals` в проекте можно использовать для получения доступа к объекту `ThisWorkbook`, `Sheet1`, `Sheet2` или `Sheet3` вне соответствующего класса. Дополнительные сведения см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md). В следующем примере вызывается <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> метод `Sheet1` независимо от того, размещен ли код в одном из `Sheet`  *n*  классы или `ThisWorkbook` класса.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Поскольку данные в документе Excel хорошо структурированы, объектная модель имеет прямую иерархическую структуру. Excel предоставляет сотни объектов, с которыми можно взаимодействовать, но лучше начать работу с запуска объектной модели и сосредоточиться на небольшом подмножестве доступных объектов. К числу этих объектов относятся следующие четыре:  
  
-   Приложение  
  
-   Workbook  
  
-   Worksheet  
  
-   Диапазон  
  
 С этими четырьмя объектами и их составляющими связана большая часть работы в Excel.  
  
### <a name="application-object"></a>Объект приложения  
 Объект Excel <xref:Microsoft.Office.Interop.Excel.Application> представляет само приложение Excel. Объект <xref:Microsoft.Office.Interop.Excel.Application> представляет множество сведений о выполняемом приложении, параметрах соответствующего экземпляра и текущих объектах пользователя, открытых в экземпляре.  
  
> [!NOTE]  
>  Не следует задавать <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> свойство <xref:Microsoft.Office.Interop.Excel.Application> в Excel значение **false**. Установка значения false для этого свойства предотвращает инициирование событий в Excel, включая события элементов управления ведущего приложения.  
  
### <a name="workbook-object"></a>Объект Workbook  
 Объект <xref:Microsoft.Office.Interop.Excel.Workbook> представляет отдельную книгу в приложении Excel.  
  
 Средства разработки Office в Visual Studio расширяют объект <xref:Microsoft.Office.Interop.Excel.Workbook>, предоставляя тип <xref:Microsoft.Office.Tools.Excel.Workbook>. Данный тип обеспечивает доступ ко всем функциям объекта <xref:Microsoft.Office.Interop.Excel.Workbook>. Для получения дополнительной информации см. [Workbook Host Item](../vsto/workbook-host-item.md).  
  
### <a name="worksheet-object"></a>Объект Worksheet  
 Объект <xref:Microsoft.Office.Interop.Excel.Worksheet> является членом коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets>. Многие свойства, методы и события объекта <xref:Microsoft.Office.Interop.Excel.Worksheet> идентичны или похожи на элементы, предоставляемые объектами <xref:Microsoft.Office.Interop.Excel.Application> или <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Excel предоставляет коллекцию <xref:Microsoft.Office.Interop.Excel.Sheets> как свойство объекта <xref:Microsoft.Office.Interop.Excel.Workbook>. Каждый член коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> является объектом <xref:Microsoft.Office.Interop.Excel.Worksheet> или <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Средства разработки Office в Visual Studio расширяют объект <xref:Microsoft.Office.Interop.Excel.Worksheet>, предоставляя тип <xref:Microsoft.Office.Tools.Excel.Worksheet>. Этот тип предоставляет доступ ко всем функциям объекта <xref:Microsoft.Office.Interop.Excel.Worksheet>, а также к новым функциям, таким как возможность размещения управляемых элементов управления и обработки новых событий. Дополнительные сведения см. в разделе [Worksheet Host Item](../vsto/worksheet-host-item.md).  
  
### <a name="range-object"></a>Range - объект  
 Объект <xref:Microsoft.Office.Interop.Excel.Range> является объектом, который используется в приложениях Excel чаще всего. Для работы с какой-либо областью Excel ее необходимо указать в качестве объекта <xref:Microsoft.Office.Interop.Excel.Range>, а затем использовать методы и свойства этого диапазона. Объект <xref:Microsoft.Office.Interop.Excel.Range> может представлять ячейку, строку или столбец, выборку ячеек, содержащую один или несколько смежных или несмежных блоков ячеек, или даже группу ячеек, распределенную между разными листами.  
  
 Visual Studio расширяет объект <xref:Microsoft.Office.Interop.Excel.Range>, предоставляя типы <xref:Microsoft.Office.Tools.Excel.NamedRange> и <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Эти типы обладают большинством функций объекта <xref:Microsoft.Office.Interop.Excel.Range>, а также новыми функциями, такими как возможность привязки данных и новые события. Дополнительные сведения см. в разделе [управления NamedRange](../vsto/namedrange-control.md) и [управления XmlMappedRange](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a>Использование документации по объектной модели Excel  
 Полные сведения об объектной модели Excel см. в справочнике по основной сборке взаимодействия (PIA) Excel и в справочнике по объектной модели VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Документация по основной сборке взаимодействия  
 В справочной документации по основной сборке взаимодействия Excel описываются типы основной сборки взаимодействия для Excel. Эта документация доступна по адресу: [Excel 2010 основной сборке взаимодействия](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 Дополнительные сведения о проектировании основных сборок взаимодействия Excel, включая различия между классами и интерфейсами в основных сборках ВЗАИМОДЕЙСТВИЯ и порядок реализации событий в этих СБОРКАХ, см. [Общие сведения о классах и интерфейсах в основных сборках взаимодействия Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### <a name="vba-object-model-reference"></a>Справочник по объектной модели VBA  
 В справочных документах по объектной модели VBA объектная модель Excel описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в разделе [Справочник по объектной модели Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и участникам основной сборки взаимодействия Excel. Например, объект листа в справочнике по объектной модели VBA соответствует <xref:Microsoft.Office.Interop.Excel.Worksheet> объекта в основной сборке ВЗАИМОДЕЙСТВИЯ Excel. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C#, если требуется использовать их в проекте Excel, создаваемом с помощью Visual Studio.  
  
### <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Решения Excel](../vsto/excel-solutions.md)|Инструкции по созданию настроек уровня документа и надстроек VSTO для Microsoft Office Excel.|  
|[Работа с диапазонами](../vsto/working-with-ranges.md)|Примеры выполнения стандартных задач с диапазонами.|  
|[Работа с листами](../vsto/working-with-worksheets.md)|Примеры выполнения стандартных задач с листами.|  
|[Работа с книгами](../vsto/working-with-workbooks.md)|Примеры выполнения стандартных задач с книгами.|  
  
  