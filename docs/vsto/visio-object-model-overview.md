---
title: Общие сведения об объектной модели Visio
description: Узнайте, как можно взаимодействовать с объектной моделью Visio для разработки решений Office для Microsoft Visio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8d7a83b5a900defb63ceffe4f63d57e2b200c47b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921770"
---
# <a name="visio-object-model-overview"></a>Общие сведения об объектной модели Visio
  Для разработки решений Office для Microsoft Office Visio вы можете взаимодействовать с объектной моделью Visio. Эта объектная модель состоит из классов и интерфейсов, которые предоставляются в основной сборке взаимодействия для Visio и определены в пространстве имен `Microsoft.Office.Interop.Visio`.

 В этом разделе приводится краткий обзор объектной модели Visio. Дополнительные сведения об использовании объектной модели Visio для выполнения задач в проектах Office см. в следующих разделах.

- [Работа с документами Visio](../vsto/working-with-visio-documents.md)

- [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Общие сведения об объектной модели Visio
 Visio предоставляет множество различных объектов, с которыми можно взаимодействовать. Они организованы в виде иерархии, которая точно соответствует пользовательскому интерфейсу. В верхней части иерархии находится объект [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) . Он представляет текущий экземпляр Visio. `Microsoft.Office.Interop.Visio.Application`Объект содержит `Microsoft.Office.Interop.Visio.Document` объекты и, а `Microsoft.Office.Interop.Visio.Page` также `Microsoft.Office.Interop.Visio.Documents` `Microsoft.Office.Interop.Visio.Pages` коллекции и. Каждый из этих объектов и коллекций содержит много методов и свойств, к которым можно обращаться для работы и взаимодействия с ними.

 Дополнительные сведения см. в справочной документации VBA для объектов [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)и [Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) , а также для коллекций [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) и [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) .

 В следующих разделах кратко описываются объекты верхнего уровня и их взаимодействие друг с другом. К числу этих объектов относятся следующие:

- Объект приложения

- объект документа;

- Page - объект

### <a name="application-object"></a>Объект приложения
 Объект Microsoft. Office. Interop. Visio. Application представляет приложение Visio и является родительским для всех других объектов. Обычно его элементы применяются к Visio как к единому целому. Для управления средой Visio можно использовать свойства и методы Microsoft. Office. Interop. Visio. Application и `Microsoft.Office.Interop.Visio.ApplicationSettings` объектов.

 В проектах надстроек VSTO доступ к объекту Microsoft. Office. Interop. Visio. Application можно получить с помощью `Application` поля `ThisAddIn` класса. Для получения дополнительной информации см. [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>объект документа;
 Объект Microsoft.Office.Interop.Visio.Docумент является центральным для программирования в Visio. Он представляет документ, набор элементов или файл шаблона. При открытии документа Visio или создании нового документа создается новый объект Microsoft.Office.Interop.Visio.Docумент, который добавляется в коллекцию Microsoft.Office.Interop.Visio.Docументс объекта Microsoft. Office. Interop. Visio. Application.

 Документ, который находится в фокусе, называется активным документом. Он представлен `Microsoft.Office.Interop.Visio.Application.ActiveDocument` свойством объекта Microsoft. Office. Interop. Visio. Application.

### <a name="page-object"></a>Page - объект
 Объект Microsoft. Office. Interop. Visio. Page представляет область рисования переднего плана или фоновой страницы. Вы можете использовать свойство `Microsoft.Office.Interop.Visio.Page.Background`, чтобы определить, является ли страница основной или фоновой.

 Для создания фигур можно использовать методы, в том числе `Microsoft.Office.Interop.Visio.Page.DrawSpline` и `Microsoft.Office.Interop.Visio.Page.DrawOval`. Кроме того, можно извлекать образцы из наборов элементов и размещать фигуры на странице с помощью метода `Microsoft.Office.Interop.Visio.Page.Drop` или `Microsoft.Office.Interop.Visio.Page.DropMany`.

## <a name="use-the-visio-object-model-documentation"></a>Использование документации по объектной модели Visio
 Полные сведения об объектной модели Visio см. в справочнике по объектной модели Visio VBA. В справочных документах по объектной модели VBA объектная модель Visio описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в [справочнике по объектной модели Visio](/office/vba/api/overview/visio/object-model).

 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и членам основной сборки взаимодействия Visio. Например, `Document` объект в справочнике по объектной модели VBA соответствует типу Microsoft.Office.Interop.Visio.Docумент в сборке PIA Visio. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C#, если требуется использовать их в проекте надстройки Visio VSTO, создаваемом с помощью Visual Studio.

> [!NOTE]
> В настоящее время справочная документация по основной сборке взаимодействия Visio отсутствует.

 Связанные примеры кода и дополнительные инструменты для создания решений Visio см. в разделе [Visio 2010 Software Development Kit](https://www.microsoft.com/download/details.aspx?id=12365).

### <a name="additional-types-in-primary-interop-assemblies"></a>Дополнительные типы в основных сборках взаимодействия
 В основных сборках взаимодействия можно найти типы, которые не видны для VBA из-за различий в реализации. VBA предоставляет представление объектной модели Visio, включающее только те объекты и члены, которые можно использовать напрямую. Основные сборки взаимодействия предоставляют такую же объектную модель, но они также содержат другие интерфейсы, классы и члены, которые преобразуют объекты объектной модели COM в управляемый код. Эти дополнительные элементы не предназначены для непосредственного использования в коде.

 Дополнительные сведения см. в разделе Общие сведения о [классах и интерфейсах в основных сборках взаимодействия Office](/previous-versions/office/office-12/ms247299(v=office.12)) и [основных сборках взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

## <a name="see-also"></a>См. также раздел
- [Решения Visio](../vsto/visio-solutions.md)
- [Работа с документами Visio](../vsto/working-with-visio-documents.md)
- [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)
