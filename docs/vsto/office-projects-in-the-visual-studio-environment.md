---
title: "Проекты Office в среде Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
ms.assetid: 4bff36c9-4edd-4b28-89e6-0ea9f6caca02
caps.latest.revision: "58"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8cf489d5a1c4246adf4f5c4220229acb05ac67d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Проекты Office в среде Visual Studio
  Разработка проектов Microsoft Office аналогична разработке в Visual Studio проектов других типов, таких как проекты Windows Forms. При создании или открытии проекта Office элементы проекта отображаются в **обозревателе решений**. Для проектов уровня документа документ (документ Word или книга Excel) открывается в среде Visual Studio и используется в качестве визуального конструктора.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="project-items-in-solution-explorer"></a>Элементы проекта в обозревателе решений  
 В проекте уровня документа в **обозревателе решений** отображаются указанные ниже элементы по умолчанию.  
  
-   Узлы документа, книги или листы, настраиваемые в рамках проекта. Эти узлы служат контейнерами для файлов кода, связанных с документом, книгой и листами.  
  
-   Файлы кода, связанные с документом, книгой и листами, которые настраиваются проектом. В проектах Word файлы кода связаны с документом или шаблоном Word. В проектах Excel файлы кода связаны с книгой или шаблоном Excel, а также с каждым листом и листом диаграммы в книге или шаблоне.  
  
-   Скрытые файлы проекта, которые не предназначены для непосредственного редактирования. Дополнительные сведения см. в разделе [Скрытые файлы проекта](#hiddenfiles).  
  
 В проекте надстройки VSTO в **обозревателе решений** отображаются указанные ниже элементы по умолчанию:  
  
-   Узел приложения. Имя этого узла совпадает с именем ведущего приложения, например **Word**, **Excel**или **Outlook**. Узел приложения содержит файл кода ThisAddIn. Он также предоставляет свойство **Пространство имен для элемента узла** . Дополнительные сведения об этом свойстве см. в разделе [Properties in Office Projects](../vsto/properties-in-office-projects.md).  
  
-   Файл кода ThisAddIn. Этот файл содержит созданный класс `ThisAddIn` для надстройки VSTO. Дополнительные сведения об этом классе см. в разделе [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Скрытые файлы проекта, которые не предназначены для непосредственного редактирования. Дополнительные сведения см. в разделе [Скрытые файлы проекта](#hiddenfiles).  
  
### <a name="temporary-certificates"></a>Временные сертификаты  
 Проекты Office также содержат временный сертификат с именем *имя_проекта*_TemporaryKey.pfx. Этот сертификат служит для подписи манифестов приложения и развертывания проекта во время разработки. Дополнительные сведения см. в разделе [Присвоение уровня доверия решениям Office](../vsto/granting-trust-to-office-solutions.md) и [обеспечение безопасности решений Office](../vsto/securing-office-solutions.md).  
  
###  <a name="hiddenfiles"></a> Скрытые файлы проекта  
 По умолчанию несколько файлов проекта скрыты. Эти файлы создаются средой Visual Studio и зависят от типа проекта. Для отображения скрытых файлов нажмите кнопку **Показать все файлы** в **обозревателе решений**.  
  
 Не вносите изменения в скрытые файлы проекта. Изменение этих файлов не поддерживается и может привести к повреждению проекта. Скрытые файлы проекта заново создаются при внесении определенных изменений в документ. Если в скрытый файл проекта внести изменения вручную, эти изменения будут потеряны при следующем создании файла.  
  
## <a name="document-designer-in-document-level-projects"></a>Конструктор документов в проектах уровня документа  
 Проекты уровня документа для приложений Excel и Word предоставляют конструктор, в котором располагаются документы, связанные с проектом в среде Visual Studio. Этот конструктор позволяет вносить изменения в документ без выхода из среды Visual Studio.  
  
 Чтобы открыть документ в конструкторе, дважды щелкните в **обозревателе решений** файл кода, связанный с документом. Например, чтобы открыть лист **Sheet1** в конструкторе проекта Excel дважды щелкните мышью файл кода **Sheet1** .  
  
 При изменении документа в конструкторе можно использовать собственные функции приложения Office. Например, можно вводить текст в документ или лист либо можно воспользоваться лентой для выполнения таких задач, как добавление таблицы или диаграммы. По умолчанию используются сочетания клавиш, заданные в среде Visual Studio. Чтобы использовать сочетания клавиш Office, измените параметры в меню **Сервис** на вкладке **Параметры** в узле **Параметры клавиатуры Microsoft Office** .  
  
### <a name="controls-on-documents"></a>Элементы управления в документах  
 *Элементы управления ведущего приложения* и элементы управления Windows Forms можно перетаскивать с панели **Панель элементов** Visual Studio в рабочую область конструирования документа. Элементы управления ведущего приложения — это специальные версии объектов Office, таких как элементы управления содержимым Word и диапазонами Excel, который могут использоваться в проектах Office, созданных с помощью Visual Studio. Ведущие элементы управления обладают дополнительными функциями, отсутствующими в объектах Office, такими как привязка данных и дополнительные события.  
  
 Дополнительные сведения см. в разделах [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) и [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Листы и книги Excel в конструкторе  
 Когда лист открыт в конструкторе, его можно изменять точно так же, как если бы он был открыт напрямую в приложении Excel. При двойном щелчке в ячейке листа она переключается в режим редактирования. Если дважды щелкнуть ячейку, в которой размещается элемент управления ведущего приложения, открывается редактор кода и среда Visual Studio создает используемый по умолчанию обработчик события для этого элемента управления. Для перехода на другие листы можно использовать вкладки листов, отображаемые в нижней части конструктора.  
  
 При открытии в конструкторе книги рабочая область конструирования отсутствует. Представление кода для книги — это большая область компонентов, заполняющая конструктор.  
  
 С книгой и с каждым ее листом связан файл кода. Каждый файл кода содержит созданный класс *ведущего элемента* , представляющий книгу или лист. Дополнительные сведения см. в разделе [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md).  
  
### <a name="word-documents-in-the-designer"></a>Документы Word в конструкторе  
 Когда документ открыт в конструкторе, его можно изменять точно так же, как если бы он был открыт напрямую в приложении Word. Если дважды щелкнуть слово в документе, это слово выделяется. Однако если слово находится в элементе управления ведущего приложения, открывается редактор кода и среда Visual Studio создает используемый по умолчанию обработчик события для этого элемента управления.  
  
 С документом связан файл кода. Файл кода содержит созданный класс *ведущего элемента* , представляющий документ. Дополнительные сведения см. в разделе [Document Host Item](../vsto/document-host-item.md).  
  
### <a name="design-mode-vs-run-time-mode"></a>Режим конструктора и режим времени выполнения  
 В среде Visual Studio документ всегда открывается в *режиме конструктора*. Некоторые задачи, такие как перетаскивание элемента управления ведущего приложения в область документа, могут выполняться только в режиме конструктора.  
  
 Чтобы просмотреть документ в *режиме времени выполнения*, необходимо открыть его в приложении вне среды Visual Studio. Также можно построить и выполнить проект. В этом случае документ автоматически открывается в приложении вне среды Visual Studio.  
  
## <a name="code-editor"></a>Редактор кода  
 Редактор кода позволяет просматривать и изменять видимые файлы кода решения. Эти файлы содержат код, определяющий поведение решения.  
  
 Дополнительные сведения о редакторе кода см. в разделе [написание кода в редакторе кода и текста](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Дополнительные сведения о написании кода в проектах Office см. в разделе [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="properties-window"></a>Окно свойств  
 В окне **Свойства** отображаются свойства элементов проекта, выбранных в **обозревателе решений**, и элементов интерфейса, выбранных в конструкторе, например свойства элементов управления или документа в проекте уровня документа. Некоторые свойства относятся к приложению или документу. Другие — ко всему проекту.  
  
## <a name="data-sources-window"></a>Окно "Источники данных"  
 Окно **Источники данных** в проектах Office уровня документа можно использовать для перетаскивания источника данных в документ и создания элемента управления, обеспечивающего привязку к источнику. Дополнительные сведения см. в разделе [привязки элементов управления к данным в Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
## <a name="see-also"></a>См. также  
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)   
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Свойства в проектах Office](../vsto/properties-in-office-projects.md)  
  
  