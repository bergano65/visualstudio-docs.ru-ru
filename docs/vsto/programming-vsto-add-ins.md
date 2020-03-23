---
title: Программа VSTO Пристыковки
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93470ebcea306d3cea762d60e061994b2bf27cc8
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79300939"
---
# <a name="program-vsto-add-ins"></a>Программа VSTO Пристыковки
  Если приложение Microsoft Office расширяется путем создания надстройки VSTO, код создается непосредственно для класса `ThisAddIn` соответствующего проекта. Этот класс можно использовать для выполнения таких задач, как получение доступа к объектной модели ведущего приложения Microsoft Office, настройка пользовательского интерфейса приложения, а также предоставление объектов созданной надстройки VSTO другим решениям Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Создание кода для надстроек VSTO несколько отличается от работы над другими типами проектов в Visual Studio. Многие отличия связаны с тем, каким образом объектные модели Office предоставляются управляемому коду. Для получения дополнительной информации смотрите [код написать в решениях Office](../vsto/writing-code-in-office-solutions.md).

 Для получения общей информации о дополнениях VSTO и других типах решений, которые вы можете создать с помощью инструментов разработки Office в Visual Studio, с [&#41;&#40;м. ](../vsto/office-solutions-development-overview-vsto.md)

## <a name="use-the-thisaddin-class"></a>Используйте класс ThisAddIn
 Создание кода надстройки VSTO начинается в классе `ThisAddIn` . Visual Studio автоматически генерирует этот класс в файле [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]кода *ThisAddIn.vb* (в) или *ThisAddIn.cs* (в C) в вашем проекте add-in. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] автоматически создает экземпляр этого класса при загрузке надстройки VSTO приложением Microsoft Office.

 В классе `ThisAddIn` существует два обработчика событий по умолчанию. Для выполнения кода при загрузке надстройки VSTO следует добавить код в обработчик событий `ThisAddIn_Startup` . Для выполнения кода непосредственно перед выгрузкой надстройки VSTO следует добавить код в обработчик событий `ThisAddIn_Shutdown` . Для получения дополнительной информации об обработчиках событий [см.](../vsto/events-in-office-projects.md)

> [!NOTE]
> В Outlook обработчик событий `ThisAddIn_Shutdown` не вызывается при каждой выгрузке надстройки VSTO по умолчанию. Для получения дополнительной информации [см.](../vsto/events-in-office-projects.md)

### <a name="access-the-object-model-of-the-host-application"></a>Доступ к объектной модели приложения-хоста
 Доступ к объектной модели ведущего приложения можно получить с помощью поля `Application` класса `ThisAddIn` . Это поле возвращает объект, представляющий текущий экземпляр ведущего приложения. В приведенной ниже таблице представлены типы возвращаемых значений для поля `Application` в каждом проекте надстройки VSTO.

|Ведущее приложение|Тип возвращаемого значения|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Приложение](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 Следующий пример кода показывает, `Application` как использовать поле для создания новой рабочей книги в add-in VSTO для Microsoft Office Excel. Код в примере должен выполняться из класса `ThisAddIn` .

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Чтобы выполнить это же действие без использования класса `ThisAddIn` , используйте для получения доступа к классу `Globals` объект `ThisAddIn` . Для получения дополнительной `Globals` информации об объекте [см.](../vsto/global-access-to-objects-in-office-projects.md)

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Дополнительные сведения об объектных моделях конкретных приложений Microsoft Office см. в следующих статьях:

- [Обзор модели объектов Excel](../vsto/excel-object-model-overview.md)

- [Обзор модели объектов слова](../vsto/word-object-model-overview.md)

- [Обзор модели объектов Outlook](../vsto/outlook-object-model-overview.md)

- [решения InfoPath](../vsto/infopath-solutions.md)

- [Решения PowerPoint](../vsto/powerpoint-solutions.md)

- [Решения проекта](../vsto/project-solutions.md)

- [Обзор модели объектов Visio](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a>Доступ к документу при запуске приложения Office
 Многие приложения [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] и ни одно приложение [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] не открывают какой-либо документ при своем запуске автоматически. Поэтому не добавляйте код `ThisAdd-In_Startup` в обработчик событий, если код требует, чтобы документ был открыт. Добавьте код в событие, которое создает приложение Office, когда пользователь создает или открывает документ. В этом случае документ точно будет открыт, прежде чем созданный вами код проведет с ним какие-то операции.

 В приведенном ниже примере код работает с документом Word только в том случае, если пользователь создает новый или открывает существующий документ.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn членов для использования для других задач
 В приведенной ниже таблице описаны наиболее распространенные задачи и члены класса `ThisAddIn` , которые можно использовать для выполнения этих задач.

|Задача|Используемый член|
|----------|-------------------|
|Выполнение кода для инициализации надстройки VSTO при ее загрузке.|Добавьте код в метод `ThisAddIn_Startup` . Этот метод является обработчиком событий по умолчанию для события <xref:Microsoft.Office.Tools.AddInBase.Startup> . Для получения дополнительной информации [см.](../vsto/events-in-office-projects.md)|
|Выполнение кода для очистки используемых надстройкой VSTO ресурсов перед выгрузкой надстройки VSTO.|Добавьте код в метод `ThisAddIn_Shutdown` . Этот метод является обработчиком событий по умолчанию для события <xref:Microsoft.Office.Tools.AddInBase.Shutdown> . Для получения дополнительной информации [см.](../vsto/events-in-office-projects.md) **Примечание:**  В Outlook по `ThisAddIn_Startup` умолчанию обработчик событий не всегда вызывается при разгрузке дополнения VSTO. Для получения дополнительной информации [см.](../vsto/events-in-office-projects.md)|
|Отображение настраиваемой области задач.|Используйте поле `CustomTaskPanes` . Для получения дополнительной информации [см.](../vsto/custom-task-panes.md)|
|Предоставление доступа к объектам в надстройке VSTO другим решениям Microsoft Office.|Переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Для получения дополнительной информации смотрите [код вызова в дополнениях VSTO из других решений Office.](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Настройка функции в системе Microsoft Office путем реализации интерфейса расширяемости.|Переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> для возврата экземпляра класса, который реализует интерфейс. Для получения дополнительной информации [см.](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md) **Примечание:**  Чтобы настроить ленточный ui, можно <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> также переопределить метод.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Понять дизайн класса ThisAddIn
 В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], интерфейсом является <xref:Microsoft.Office.Tools.AddIn> . Класс `ThisAddIn` является производным от класса <xref:Microsoft.Office.Tools.AddInBase> . Этот базовый класс перенаправляет все вызовы к членам внутренней реализации интерфейса <xref:Microsoft.Office.Tools.AddIn> в [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

 В проектах надстроек VSTO для Outlook класс `ThisAddIn` является производным от класса `Microsoft.Office.Tools.Outlook.OutlookAddIn` в проектах, предназначенных для .NET Framework 3.5, или от класса <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Эти базовые классы предоставляют дополнительные функции для поддержки областей форм. Для получения дополнительной информации [Create Outlook form regions](../vsto/creating-outlook-form-regions.md)о регионах формы см.

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Настройка пользовательского интерфейса приложений Microsoft Office
 Используя надстройку VSTO, можно настроить пользовательский интерфейс для приложений Microsoft Office программными средствами. Например, можно настроить ленту таким образом, чтобы в ней отображалась настраиваемая панель задач, или создать настраиваемую область формы в Outlook. Для получения дополнительной [Office UI customization](../vsto/office-ui-customization.md)информации см.

 Visual Studio предоставляет конструкторы и классы, которые можно использовать для создания настраиваемых областей задач, настроек ленты и областей формы Outlook. Такие конструкторы и классы упрощают процесс настройки этих функций. Для получения дополнительной информации [см. пользовательские панели задач,](../vsto/custom-task-panes.md) [дизайнер ленты](../vsto/ribbon-designer.md)и [создать Outlook образуют регионы.](../vsto/creating-outlook-form-regions.md)

 Если какую-то из этих функций необходимо настроить способом, который не поддерживается классами и конструкторами, можно реализовать эти функции в надстройке VSTO *интерфейса расширяемости* . Для получения дополнительной информации [см.](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)

 Кроме того, можно изменить пользовательский интерфейс документов Word и книг Excel, создавая ведущие элементы, которые расширяют поведение документов и книг. Это позволяет добавлять управляемые элементы управления в документы и листы. Для получения дополнительной информации смотрите [документы Extend Word и рабочие книги Excel в надстройки VSTO во время выполнения.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Код вызова в надстройки VSTO от других решений
 Доступ к объектам в надстройке VSTO можно предоставлять другим решениям, включая решения Office. Это полезно, если надстройка VSTO предоставляет службу, доступ к которой нужно предоставить другим решениям. Например, если у вас есть VSTO Add-in для Microsoft Office Excel, который выполняет расчеты по финансовым данным из веб-службы, другие решения могут выполнять эти вычисления, вызывая в Excel VSTO Add-in во время выполнения.

 Для получения дополнительной информации смотрите [код вызова в дополнениях VSTO из других решений Office.](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)

## <a name="see-also"></a>См. также раздел
- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Расширить документы Word и рабочие книги Excel в надстройки VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Код вызова в надстройке VSTO от других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Пошаговое: Код вызова в add-in VSTO от VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Настройка функций uI с помощью интерфейсов расширяемости](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Как: Создать офисные проекты в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Запись кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
