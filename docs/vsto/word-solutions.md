---
title: решения Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0c34ea0489801a563745047b920e38afe58aec1c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445491"
---
# <a name="word-solutions"></a>решения Word
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания настроек на уровне документа и надстроек VSTO для Microsoft Office Word. Эти решения можно использовать для автоматизации Word, расширения функциональных возможностей Word и настройки пользовательского интерфейса Word. Дополнительные сведения о различиях между настройками уровня документа и надстроек VSTO см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

> [!NOTE]
> Занимаетесь разработкой решений, расширяющих возможности Office по [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и вы можете создавать их с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.

 В данном разделе содержатся следующие сведения:

- [Автоматизация Word](#automating).

- [Разработка настроек на уровне документа для Word](#doclevel).

- [Разработка надстроек VSTO для Word](#applevel).

- [Настройка пользовательского интерфейса Word](#UI).

## <a name="automating"></a> Автоматизация Word
 Объектная модель Word предоставляет различные типы, которые можно использовать для автоматизации Word. Например, можно программным образом создавать таблицы, форматировать документы и задавать текст в диапазонах и абзацах. Дополнительные сведения см. в разделе [обзор объектной модели Word](../vsto/word-object-model-overview.md).

 При разработке своих решений Word в Visual Studio можно также использовать *ведущие элементы* и *элементы управления ведущего приложения* . Данные элементы являются объектами, которые расширяют некоторые часто используемые объекты в объектной модели Word, например объекты <xref:Microsoft.Office.Interop.Word.Document> и <xref:Microsoft.Office.Interop.Word.ContentControl> . Расширенные объекты ведут себя как объекты Word, на которых они основаны, но добавляют объектам дополнительные события и возможности по привязке данных. Дополнительные сведения см. в разделе [автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md).

## <a name="doclevel"></a> Разработка настроек на уровне документа для Word
 Настройка на уровне документа для Microsoft Office Word состоит из сборки, связанной с конкретным документом. Как правило, сборка расширяет документ посредством настройки пользовательского интерфейса и автоматизации Word. В отличие от надстройки VSTO, которая связана с самим Word, функциональные возможности, реализуемые в настройке, доступны только в том случае, когда соответствующий документ открыт в Word.

 Для создания проекта настройки на уровне документа для Word используйте шаблоны проектов для документа Word или шаблона Word в диалоговом окне **Новый проект** Visual Studio. Дополнительные сведения см. в разделе [Как Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Дополнительные сведения о работе настроек на уровне документа [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).

### <a name="word-customization-programming-model"></a>Модель программирования настройки Word
 При создании проекта на уровне документа для Word Visual Studio создает класс с именем `ThisDocument`, который служит базой для вашего решения. Этот класс представляет документ, связанный с решением, и служит отправной точкой для написания собственного кода.

 Дополнительные сведения о `ThisDocument` класса и другие функции, можно использовать в проекте уровня документа см. в разделе [программирование настроек уровня документа](../vsto/programming-document-level-customizations.md).

## <a name="applevel"></a> Разработка надстроек VSTO для Word
 Надстройка VSTO для Microsoft Office Word состоит из сборки, загружаемой в Word. Как правило, сборка расширяет Word посредством настройки пользовательского интерфейса и автоматизации Word. В отличие от настройки уровня документа, которая связана с конкретным документом, функциональные возможности, реализуемые в надстройке VSTO не привязана к отдельным документом.

 Для создания проекта надстройки VSTO для Word используйте шаблоны проектов надстройки Word в диалоговом окне **Новый проект** Visual Studio. Дополнительные сведения см. в разделе [Как Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Общие сведения о работе надстроек VSTO см. в разделе [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="word-add-in-programming-model"></a>Word-модели программирования надстроек
 При создании проекта надстройки VSTO для Word среда Visual Studio создает класс с именем `ThisAddIn`, который служит базой для вашего решения. Этот класс служит отправной точкой для написания собственного кода, а также предоставляет объектную модель Word для надстройки VSTO.

 Дополнительные сведения о `ThisAddIn` класса и другие функции, можно использовать в надстройке VSTO, см. в разделе [программы VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

## <a name="UI"></a> Настройка пользовательского интерфейса Word
 Для настройки пользовательского интерфейса Word можно использовать несколько способов. Некоторые параметры доступны для всех типов проектов. Также есть параметры, доступные только для надстроек VSTO или настроек на уровне документа.

### <a name="options-for-all-project-types"></a>Параметры для всех типов проектов
 В следующей таблице перечислены параметры настройки, доступные для настроек на уровне документа и надстроек VSTO.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Настройка ленты.|[Обзор ленты](../vsto/ribbon-overview.md)|
|Добавление элементов управления Windows Forms или расширенных элементов управления Word в настраиваемый документ (для настройки на уровне документа) или в любой открытый документ (для надстройки VSTO).|[Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Практическое руководство. Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Практическое руководство. Добавление элементов управления bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|

### <a name="options-for-document-level-customizations"></a>Параметры для настроек уровня документа
 В следующей таблице перечислены параметры настройки, доступные только для настроек на уровне документа.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Добавление панели действий в документ.|[Общие сведения о панели действий](../vsto/actions-pane-overview.md)<br /><br /> [Практическое руководство. Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Добавление расширенных элементов управления XMLNode и XMLNodes на поверхность документа.|[Практическое руководство. Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Практическое руководство. Добавление элементов управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|

### <a name="options-for-vsto-add-ins"></a>Параметры для надстроек VSTO
 В следующей таблице перечислены параметры настройки, доступные только для надстроек VSTO.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Создание настраиваемой области задач.|[Настраиваемые области задач](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Обзор объектной модели Word](../vsto/word-object-model-overview.md)|Содержит общие сведения об основных типах, предоставляемых объектной моделью Word.|
|[Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)|Содержит сведения о расширенных объектах (предоставляемых из [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), которые можно использовать в решениях Word.|
|[Элементы управления Windows Forms на общие сведения о документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Содержит сведения о добавлении элементов управления Windows Forms в документы Word.|
|[Пошаговое руководство: Создание первой настройки уровня документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Содержит сведения о создании базовой настройки на уровне документа для Word.|
|[Пошаговое руководство: Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Содержит сведения о создании базовой надстройки VSTO для Word.|
|[Пошаговое руководство: Добавление элементов управления в документ во время выполнения в надстройке VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Содержит сведения о добавлении кнопки Windows Forms и <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в документ во время выполнения с помощью надстройки VSTO.|
|[Word 2010 при разработке решений Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Содержит ссылки на статьи и справочную документацию о разработке решений Word (не только о разработке решений Office с помощью Visual Studio).|
