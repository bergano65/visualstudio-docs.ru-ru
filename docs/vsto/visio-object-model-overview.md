---
title: Общие сведения о модели объектов Visio | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e77256d800cb23b61a6680cdf59e60a39c7b57e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="visio-object-model-overview"></a>Общие сведения об объектной модели Visio
  Для разработки решений Office для Microsoft Office Visio вы можете взаимодействовать с объектной моделью Visio. Эта объектная модель состоит из классов и интерфейсов, которые предоставляются в основной сборке взаимодействия для Visio и определены в пространстве имен Microsoft.Office.Interop.Visio.  
  
 В этом разделе приводится краткий обзор объектной модели Visio. Дополнительные сведения об использовании объектной модели Visio для выполнения задач в проектах Office см. в следующих разделах.  
  
-   [Работа с документами Visio](../vsto/working-with-visio-documents.md)  
  
-   [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)  
  
## <a name="understanding-the-visio-object-model"></a>Основные сведения об объектной модели Visio  
 Visio предоставляет множество различных объектов, с которыми можно взаимодействовать. Они организованы в виде иерархии, которая точно соответствует пользовательскому интерфейсу. В верхней части иерархии находится объект [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx) . Он представляет текущий экземпляр Visio. Объект Microsoft.Office.Interop.Visio.Application содержит объекты Microsoft.Office.Interop.Visio.Document и Microsoft.Office.Interop.Visio.Page, а также Microsoft.Office.Interop.Visio.Documents и Microsoft.Office.Interop.Visio.Pages коллекции. Каждый из этих объектов и коллекций содержит много методов и свойств, к которым можно обращаться для работы и взаимодействия с ними.  
  
 Дополнительные сведения см. в справочной документации VBA для объектов [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx), [Microsoft.Office.Interop.Visio.Document](https://msdn.microsoft.com/library/office/ff765575.aspx)и [Microsoft.Office.Interop.Visio.Page](https://msdn.microsoft.com/library/office/ff767035.aspx) , а также для коллекций [Microsoft.Office.Interop.Visio.Documents](https://msdn.microsoft.com/library/office/ff768812.aspx) и [Microsoft.Office.Interop.Visio.Pages](https://msdn.microsoft.com/library/office/ff766165.aspx) .  
  
 В следующих разделах кратко описываются объекты верхнего уровня и их взаимодействие друг с другом. К числу этих объектов относятся следующие:  
  
-   объект приложения;  
  
-   объект документа;  
  
-   Page - объект  
  
### <a name="application-object"></a>объект приложения;  
 Объект Microsoft.Office.Interop.Visio.Application представляет приложение Visio и является родителем для всех других объектов. Обычно его элементы применяются к Visio как к единому целому. Свойства и методы Microsoft.Office.Interop.Visio.Application и Microsoft.Office.Interop.Visio.ApplicationSettings объектов можно использовать для управления средой Visio.  
  
 В проектах надстройки VSTO, можно получить доступ к объекту Microsoft.Office.Interop.Visio.Application с помощью `Application` поле `ThisAddIn` класса. Для получения дополнительной информации см. [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
### <a name="document-object"></a>Объект Document  
 Microsoft.Office.Interop.Visio.Document это центральный объект для программирования в Visio. Он представляет документ, набор элементов или файл шаблона. При открытии существующего документа Visio или создании нового документа, создания нового объекта Microsoft.Office.Interop.Visio.Document, который добавляется в коллекцию Microsoft.Office.Interop.Visio.Documents Microsoft.Office.Interop.Visio.Application объекта .  
  
 Документ, который находится в фокусе, называется активным документом. Он представлен свойством Microsoft.Office.Interop.Visio.Application.ActiveDocument Microsoft.Office.Interop.Visio.Application объекта.  
  
### <a name="page-object"></a>Page - объект  
 Объект Microsoft.Office.Interop.Visio.Page представляет область рисования основной или фоновой страницы. Свойство Microsoft.Office.Interop.Visio.Page.Background определить, является ли страница основной или фоновой страницы.  
  
 Для создания фигур можно использовать методы, которые включают в себя методы Microsoft.Office.Interop.Visio.Page.DrawSpline и Microsoft.Office.Interop.Visio.Page.DrawOval. Кроме того можно извлекать образцы из наборов элементов и размещать фигуры на странице с помощью методов Microsoft.Office.Interop.Visio.Page.Drop или Microsoft.Office.Interop.Visio.Page.DropMany.  
  
## <a name="using-the-visio-object-model-documentation"></a>Работа с документацией по объектной модели Visio  
 Полные сведения об объектной модели Visio см. в справочнике по объектной модели Visio VBA. В справочных документах по объектной модели VBA объектная модель Visio описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в разделе [Справочник по объектной модели Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и членам основной сборки взаимодействия Visio. Например объект документа в справочнике по объектной модели VBA соответствует типу Microsoft.Office.Interop.Visio.Document в основной сборке ВЗАИМОДЕЙСТВИЯ Visio. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C#, если требуется использовать их в проекте надстройки Visio VSTO, создаваемом с помощью Visual Studio.  
  
> [!NOTE]  
>  В настоящее время справочная документация по основной сборке взаимодействия Visio отсутствует.  
  
 Соответствующие примеры кода и сведения о дополнительных средствах для создания решений Visio см. в разделе [Пакет SDK для Visio 2010](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>Дополнительные типы в основных сборках взаимодействия  
 В основных сборках взаимодействия можно найти типы, которые не видны для VBA из-за различий в реализации. VBA предоставляет представление объектной модели Visio, включающее только те объекты и члены, которые можно использовать напрямую. Основные сборки взаимодействия предоставляют такую же объектную модель, но они также содержат другие интерфейсы, классы и члены, которые преобразуют объекты объектной модели COM в управляемый код. Эти дополнительные элементы не предназначены для непосредственного использования в коде.  
  
 Дополнительные сведения см. в разделе [Общие сведения о классах и интерфейсах в основных сборках взаимодействия Office](http://go.microsoft.com/fwlink/?LinkId=189592) и [Office Primary Interop Assemblies](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Работа с документами Visio](../vsto/working-with-visio-documents.md)   
 [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)  
  
  