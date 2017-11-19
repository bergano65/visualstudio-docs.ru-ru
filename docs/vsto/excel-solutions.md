---
title: "Решения Excel | Документы Microsoft"
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
ms.assetid: 34444d54-d7b6-479a-b5b7-a946267081e9
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 46f484bc9dc597bc43ea4e7e2474d5b7efcb1f3c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="excel-solutions"></a>Решения Excel
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания настроек на уровне документа и надстроек VSTO для Microsoft Office Excel. Эти решения можно использовать для автоматизации Excel, расширения функциональных возможностей Excel и настройки пользовательского интерфейса Excel. Дополнительные сведения о различиях между настроек на уровне документа и надстроек VSTO см. в разделе [Общие сведения о разработке решений Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Заинтересованы в разработке решений, расширяющих возможности Office через [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и их можно создавать с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
 В данном разделе содержатся следующие сведения:  
  
-   [Автоматизация Excel](#automating).  
  
-   [Разработка настроек на уровне документа для Excel](#doclevel).  
  
-   [Разработка надстроек VSTO для Excel](#applevel).  
  
-   [Настройка пользовательского интерфейса Excel](#UI).  
  
##  <a name="automating"></a> Автоматизация Excel  
 Объектная модель Excel предоставляет различные типы, которые можно использовать для автоматизации Excel. Например, можно программно создавать диаграммы, форматировать листы и задавать значения диапазонов и ячеек. Дополнительные сведения см. в разделе [Excel Object Model Overview](../vsto/excel-object-model-overview.md).  
  
 При разработке своих решений Excel в Visual Studio можно также использовать *ведущие элементы* и *элементы управления ведущего приложения* . Данные элементы являются объектами, которые расширяют некоторые часто используемые объекты в объектной модели Excel, например объекты <xref:Microsoft.Office.Interop.Excel.Worksheet> и <xref:Microsoft.Office.Interop.Excel.Range> . Расширенные объекты ведут себя как объекты Excel, на которых они основаны, но добавляют объектам дополнительные события и возможности по привязке данных. Дополнительные сведения см. в разделе [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Developing Document-Level Customizations for Excel  
 Настройка на уровне документа для Microsoft Office Excel состоит из сборки, связанной с конкретной книгой. Как правило, сборка расширяет книгу посредством настройки пользовательского интерфейса и автоматизации Excel. В отличие от надстройки VSTO, которая связана с самим приложением Excel, функциональные возможности, реализуемые в настройке, доступны только в том случае, когда соответствующая книга открыта в Excel.  
  
 Для создания проекта настройки на уровне документа для Excel используйте шаблон проектов книги Excel или шаблон Excel в диалоговом окне **Новый проект** в Visual Studio. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Дополнительные сведения о работе настроек на уровне документа см. в разделе [Architecture of Document-Level Customizations](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="excel-customization-programming-model"></a>Модель программирования настройки Excel  
 При создании проекта на уровне документа для Excel Visual Studio создает несколько классов, которые служат базой для вашего решения: `ThisWorkbook`, `Sheet1`, `Sheet2`и `Sheet3`. Эти классы представляют книгу и листы, связанные с решением, а также отправную точку для написания кода.  
  
 Дополнительные сведения об этих создаваемых классах и других возможностях, которые можно использовать в проекте на уровне документа, см. в разделе [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Разработка надстроек VSTO для Excel  
 Надстройка VSTO для Microsoft Office Excel состоит из сборки, загружаемой в Excel. Как правило, сборка расширяет Excel посредством настройки пользовательского интерфейса и автоматизации Excel. В отличие от настройки на уровне документа, связанной с конкретной книгой, функциональные возможности, реализуемые в надстройке VSTO, не ограничиваются отдельной книгой.  
  
 Для создания проекта настройки VSTO для Excel используйте шаблон книги Excel или шаблон проекта Excel в диалоговом окне **Новый проект** в Visual Studio. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Общие сведения о работе надстроек VSTO см. в разделе [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как автоматизировать PowerPoint из надстройки Excel?](http://go.microsoft.com/fwlink/?LinkID=130300).  
  
### <a name="excel-add-in-programming-model"></a>Модель программирования надстроек Excel  
 При создании проекта надстройки VSTO Excel Visual Studio создает класс с именем `ThisAddIn`, который служит базой для вашего решения. Этот класс представляет отправную точку для написания собственного кода, а также предоставляет объектную модель Excel для надстройки VSTO.  
  
 Дополнительные сведения о классе `ThisAddIn` и других функциональных возможностях Visual Studio, которые можно использовать в надстройке VSTO, см. в разделе [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Customizing the User Interface of Excel  
 Для настройки пользовательского интерфейса Excel можно использовать несколько способов. Некоторые параметры доступны для всех типов проектов. Также есть параметры, доступные только для надстроек VSTO или настроек на уровне документа.  
  
### <a name="options-for-all-project-types"></a>Параметры для всех типов проектов  
 В следующей таблице перечислены параметры настройки, доступные для настроек на уровне документа и надстроек VSTO.  
  
|Задача|Дополнительные сведения|  
|----------|--------------------------|  
|Настройка ленты.|[Обзор ленты](../vsto/ribbon-overview.md)|  
|Добавление элементов управления Windows Forms или расширенных элементов управления Excel на лист в настраиваемой книге для настройки на уровне документа или в любой открытый документ для надстройки VSTO.|[Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Практическое руководство. Добавление элементов управления Chart на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-document-level-customizations"></a>Параметры для настроек на уровне документа  
 В следующей таблице перечислены параметры настройки, доступные только для настроек на уровне документа.  
  
|Задача|Дополнительные сведения|  
|----------|--------------------------|  
|Добавление панели действий в книгу.|[Общие сведения о панели действий](../vsto/actions-pane-overview.md)<br /><br /> [Практическое руководство. Добавление области действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Добавление расширенных элементов управления диапазоном, сопоставленных с XML-узлами, на лист.|[Практическое руководство. Добавление элементов управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Параметры для надстроек VSTO  
 В следующей таблице перечислены параметры настройки, доступные только для надстроек VSTO.  
  
|Задача|Дополнительные сведения|  
|----------|--------------------------|  
|Создание настраиваемой области задач.|[Настраиваемые области задач](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Excel Object Model Overview](../vsto/excel-object-model-overview.md)|Содержит общие сведения об основных типах, предоставляемых объектной моделью Excel.|  
|[Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)|Содержит сведения о расширенных объектах (предоставляемых из [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), которые можно использовать в решениях Excel.|  
|[Глобализация и локализация решений Excel](../vsto/globalization-and-localization-of-excel-solutions.md)|Содержит сведения об особенностях решений Excel, которые будут выполняться на компьютерах с локализованными настройками для Windows.|  
|[Общие сведения об использовании элементов управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Содержит сведения о добавлении элементов управления Windows Forms на листы Excel.|  
|[Пошаговое руководство. Создание первой настройки на уровне документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Содержит сведения о создании базовой настройки на уровне документа для Excel.|  
|[Пошаговое руководство. Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Содержит сведения о создании базовой надстройки VSTO для Excel.|  
|[Пошаговое руководство. Добавление элементов управления на лист во время выполнения в проекте надстройки VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|Содержит сведения о добавлении кнопки Windows Forms, <xref:Microsoft.Office.Tools.Excel.NamedRange>, и <xref:Microsoft.Office.Tools.Excel.ListObject> на лист во время выполнения с помощью надстройки VSTO.|
|[Основные сведения о Соавторство и надстройки](./understanding-coauthoring-and-addins.md)|Описывает изменения, которые может потребоваться внести решения для размещения Соавторство.|  
|[Excel 2010 при разработке решений для Office](http://go.microsoft.com/fwlink/?LinkId=199011)|Ссылки на статьи и справочную документацию о разработке решений Excel. Они не относятся к разработке решений Office в Visual Studio.|  
  
  