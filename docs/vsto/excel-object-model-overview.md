---
title: "Общие сведения об объектной модели Excel"
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
  - "Excel - объектная модель"
  - "модели объектов [разработка решений Office в Visual Studio], Excel"
  - "модели объектов [разработка решений Office в Visual Studio], Office"
  - "объекты [разработка решений Office в Visual Studio], Office - объектные модели"
  - "Office - объектные модели"
  - "Range - объект"
  - "Workbook - класс"
  - "Worksheet - объект"
ms.assetid: e4b2e46b-ea6c-4a88-a416-a7d4f495fc33
caps.latest.revision: 66
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 65
---
# Общие сведения об объектной модели Excel
  Для разработки решений, использующих Microsoft Office Excel, необходимо взаимодействие с объектами, предоставляемыми объектной моделью Excel.  В этом разделе представлены наиболее важные объекты:  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Объектная модель точно соответствует пользовательскому интерфейсу.  Объект <xref:Microsoft.Office.Interop.Excel.Application> представляет приложение в целом, а каждый из объектов <xref:Microsoft.Office.Interop.Excel.Workbook> содержит коллекцию объектов `Worksheet`.  Отсюда следует, что основная абстракция, представляющая ячейки, является объектом <xref:Microsoft.Office.Interop.Excel.Range>, позволяющим работать с отдельными ячейками или группой ячеек.  
  
 Помимо объектной модели Excel, проекты Office в Visual Studio предоставляют *ведущие элементы* и *элементы управления ведущего приложения*, расширяющие некоторые объекты из объектной модели Excel.  Поведение ведущих элементов и элементов управления ведущего приложения аналогично поведению объектов Excel, однако они обладают дополнительными функциональными возможностями, такими как возможность привязки данных и дополнительные события.  Дополнительные сведения см. в разделах [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md) и [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
 В этом разделе приводится краткий обзор объектной модели Excel.  Список документации для более глубокого изучения объектной модели Excel см. в разделе [Использование документации по объектной модели Excel](#ExcelOMDocumentation).  
  
 ![ссылка на видео](../vsto/media/playvideo.png "ссылка на видео") Демонстрационные видеоматериалы см. в разделах [Как использовать обработчики событий в надстройках Excel 2007?](http://go.microsoft.com/fwlink/?LinkID=130291) и [Как создавать формы для пузырьковых диаграмм в Excel?](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## Доступ к объектам в проекте Excel  
 При создании нового проекта надстройки VSTO для Excel среда Visual Studio автоматически создает файл кода ThisAddIn.vb или ThisAddIn.cs.  Доступ к объекту приложения можно получить с помощью свойства `Me.Application` или `this.Application`.  
  
 При создании нового проекта уровня документа для Excel можно создать новый проект книги Excel или шаблона Excel.  Visual Studio автоматически создает в новом проекте Excel \(как для проектов книги, так и для проектов шаблона\) следующие файлы кода:  
  
|Visual Basic|C\#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 Класс `Globals` в проекте можно использовать для получения доступа к объекту `ThisWorkbook`, `Sheet1`, `Sheet2` или `Sheet3` вне соответствующего класса.  Дополнительные сведения см. в разделе [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).  В приведенном ниже примере метод <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> класса `Sheet1` вызывается независимо от того, размещен ли код в одном из классов `Sheet`*n* или в классе `ThisWorkbook`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#82)]  
  
 Поскольку данные в документе Excel хорошо структурированы, объектная модель имеет прямую иерархическую структуру.  Excel предоставляет сотни объектов, с которыми можно взаимодействовать, но лучше начать работу с запуска объектной модели и сосредоточиться на небольшом подмножестве доступных объектов.  К числу этих объектов относятся следующие четыре:  
  
-   Приложение  
  
-   Workbook  
  
-   Worksheet  
  
-   Диапазон  
  
 С этими четырьмя объектами и их составляющими связана большая часть работы в Excel.  
  
### Объект приложения  
 Объект Excel <xref:Microsoft.Office.Interop.Excel.Application> представляет само приложение Excel.  Объект <xref:Microsoft.Office.Interop.Excel.Application> представляет множество сведений о выполняемом приложении, параметрах соответствующего экземпляра и текущих объектах пользователя, открытых в экземпляре.  
  
> [!NOTE]  
>  Не устанавливайте для свойства <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> объекта <xref:Microsoft.Office.Interop.Excel.Application> в Excel значение **false**.  Установка значения false для этого свойства предотвращает инициирование событий в Excel, включая события элементов управления ведущего приложения.  
  
### Объект Workbook  
 Объект <xref:Microsoft.Office.Interop.Excel.Workbook> представляет отдельную книгу в приложении Excel.  
  
 Средства разработки Office в Visual Studio расширяют объект <xref:Microsoft.Office.Interop.Excel.Workbook>, предоставляя тип <xref:Microsoft.Office.Tools.Excel.Workbook>.  Данный тип обеспечивает доступ ко всем функциям объекта <xref:Microsoft.Office.Interop.Excel.Workbook>.  Дополнительные сведения см. в разделе [Ведущий элемент книги](../vsto/workbook-host-item.md).  
  
### Объект Worksheet  
 Объект <xref:Microsoft.Office.Interop.Excel.Worksheet> является членом коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets>.  Многие свойства, методы и события объекта <xref:Microsoft.Office.Interop.Excel.Worksheet> идентичны или похожи на элементы, предоставляемые объектами <xref:Microsoft.Office.Interop.Excel.Application> или <xref:Microsoft.Office.Interop.Excel.Workbook>.  
  
 Excel предоставляет коллекцию <xref:Microsoft.Office.Interop.Excel.Sheets> как свойство объекта <xref:Microsoft.Office.Interop.Excel.Workbook>.  Каждый член коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> является объектом <xref:Microsoft.Office.Interop.Excel.Worksheet> или <xref:Microsoft.Office.Interop.Excel.Chart>.  
  
 Средства разработки Office в Visual Studio расширяют объект <xref:Microsoft.Office.Interop.Excel.Worksheet>, предоставляя тип <xref:Microsoft.Office.Tools.Excel.Worksheet>.  Этот тип предоставляет доступ ко всем функциям объекта <xref:Microsoft.Office.Interop.Excel.Worksheet>, а также к новым функциям, таким как возможность размещения управляемых элементов управления и обработки новых событий.  Дополнительные сведения см. в разделе [Ведущие элементы листа](../vsto/worksheet-host-item.md).  
  
### Объект Range  
 Объект <xref:Microsoft.Office.Interop.Excel.Range> является объектом, который используется в приложениях Excel чаще всего.  Для работы с какой\-либо областью Excel ее необходимо указать в качестве объекта <xref:Microsoft.Office.Interop.Excel.Range>, а затем использовать методы и свойства этого диапазона.  Объект <xref:Microsoft.Office.Interop.Excel.Range> может представлять ячейку, строку или столбец, выборку ячеек, содержащую один или несколько смежных или несмежных блоков ячеек, или даже группу ячеек, распределенную между разными листами.  
  
 Visual Studio расширяет объект <xref:Microsoft.Office.Interop.Excel.Range>, предоставляя типы <xref:Microsoft.Office.Tools.Excel.NamedRange> и <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>.  Эти типы обладают большинством функций объекта <xref:Microsoft.Office.Interop.Excel.Range>, а также новыми функциями, такими как возможность привязки данных и новые события.  Дополнительные сведения см. в разделах [Элемент управления NamedRange](../vsto/namedrange-control.md) и [Элемент управления XmlMappedRange](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Использование документации по объектной модели Excel  
 Полные сведения об объектной модели Excel см. в справочнике по основной сборке взаимодействия \(PIA\) Excel и в справочнике по объектной модели VBA.  
  
### Документация по основной сборке взаимодействия  
 В справочной документации по основной сборке взаимодействия Excel описываются типы основной сборки взаимодействия для Excel.  Эта документация доступна по следующей ссылке: [Справочник по основной сборке взаимодействия Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 Дополнительные сведения о проектировании основных сборок взаимодействия Excel, включая различия между классами и интерфейсами в основных сборках взаимодействия и порядок реализации событий в этих сборках, см. в разделе [Общие сведения о классах и интерфейсах в основных сборках взаимодействия Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### Справочник по объектной модели VBA  
 В справочных документах по объектной модели VBA объектная модель Excel описана в том виде, в котором она предоставляется коду Visual Basic для приложений.  Дополнительные сведения см. в разделе [Справочник по объектной модели Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и участникам основной сборки взаимодействия Excel.  Например, объект Worksheet в справочнике по объектной модели VBA соответствует объекту <xref:Microsoft.Office.Interop.Excel.Worksheet> в основной сборке взаимодействия Excel.  Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C\#, если требуется использовать их в проекте Excel, создаваемом с помощью Visual Studio.  
  
### См. также  
  
|Заголовок|Описание|  
|---------------|--------------|  
|[Решения Excel](../vsto/excel-solutions.md)|Инструкции по созданию настроек уровня документа и надстроек VSTO для Microsoft Office Excel.|  
|[Работа с диапазонами](../vsto/working-with-ranges.md)|Примеры выполнения стандартных задач с диапазонами.|  
|[Работа с листами](../vsto/working-with-worksheets.md)|Примеры выполнения стандартных задач с листами.|  
|[Работа с книгами](../vsto/working-with-workbooks.md)|Примеры выполнения стандартных задач с книгами.|  
  
  