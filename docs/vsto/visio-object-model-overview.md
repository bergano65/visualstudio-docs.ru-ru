---
title: "Общие сведения об объектной модели Visio"
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
  - "Visio [разработка решений Office в Visual Studio], объектная модель"
  - "объектные модели [разработка решений Office в Visual Studio], Office"
  - "объектные модели [разработка решений Office в Visual Studio], Visio"
  - "объекты [разработка решений Office в Visual Studio], объектные модели Office"
  - "Office - объектные модели"
  - "объектная модель Visio"
ms.assetid: 11f0ae0c-feff-46c7-9885-b968391718f7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Общие сведения об объектной модели Visio
  Для разработки решений Office для Microsoft Office Visio вы можете взаимодействовать с объектной моделью Visio. Эта объектная модель состоит из классов и интерфейсов, которые предоставляются в основной сборке взаимодействия для Visio и определены в пространстве имен Microsoft.Office.Interop.Visio.  
  
 В этом разделе приводится краткий обзор объектной модели Visio. Дополнительные сведения об использовании объектной модели Visio для выполнения задач в проектах Office см. в следующих разделах.  
  
-   [Работа с документами Visio](../vsto/working-with-visio-documents.md)  
  
-   [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)  
  
## Основные сведения об объектной модели Visio  
 Visio предоставляет множество различных объектов, с которыми можно взаимодействовать. Они организованы в виде иерархии, которая точно соответствует пользовательскому интерфейсу. В верхней части иерархии находится объект [Microsoft.Office.Interop.Visio.Application](HV10077088). Он представляет текущий экземпляр Visio. Объект Microsoft.Office.Interop.Visio.Application содержит объекты Microsoft.Office.Interop.Visio.Document и Microsoft.Office.Interop.Visio.Page , а также коллекции Microsoft.Office.Interop.Visio.Documents и Microsoft.Office.Interop.Visio.Pages. Каждый из этих объектов и коллекций содержит много методов и свойств, к которым можно обращаться для работы и взаимодействия с ними.  
  
 Дополнительные сведения см. в справочной документации VBA для объектов [Microsoft.Office.Interop.Visio.Application](HV10077088), [Microsoft.Office.Interop.Visio.Document](HV10077095) и [Microsoft.Office.Interop.Visio.Page](HV10077063), а также для коллекций [Microsoft.Office.Interop.Visio.Documents](HV10077062) и [Microsoft.Office.Interop.Visio.Pages](HV10077074).  
  
 В следующих разделах кратко описываются объекты верхнего уровня и их взаимодействие друг с другом. К числу этих объектов относятся следующие:  
  
-   объект приложения;  
  
-   объект документа;  
  
-   Page \- объект  
  
### Объект приложения  
 Объект Microsoft.Office.Interop.Visio.Application представляет приложение Visio и является родителем для всех других объектов. Обычно его элементы применяются к Visio как к единому целому. Свойства и методы объектов Microsoft.Office.Interop.Visio.Application и Microsoft.Office.Interop.Visio.ApplicationSettings можно использовать для управления средой Visio.  
  
 В проектах надстройки VSTO для получения доступа к объекту Microsoft.Office.Interop.Visio.Application можно использовать поле `Application` класса `ThisAddIn`. Дополнительные сведения см. в разделе [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
### Объект Document  
 Microsoft.Office.Interop.Visio.Document — это центральный объект для программирования в Visio. Он представляет документ, набор элементов или файл шаблона. При открытии существующего документа Visio или создании нового документа вы создаете новый объект Microsoft.Office.Interop.Visio.Document, который добавляется в коллекцию Microsoft.Office.Interop.Visio.Documents объекта Microsoft.Office.Interop.Visio.Application.  
  
 Документ, который находится в фокусе, называется активным документом. Он представлен свойством Microsoft.Office.Interop.Visio.Application.ActiveDocument объекта Microsoft.Office.Interop.Visio.Application.  
  
### Объект страницы  
 Объект Microsoft.Office.Interop.Visio.Page представляет область рисования основной или фоновой страницы. Вы можете использовать свойство Microsoft.Office.Interop.Visio.Page.Background, чтобы определить, является ли страница основной или фоновой.  
  
 Для создания фигур можно использовать методы, в том числе Microsoft.Office.Interop.Visio.Page.DrawSpline и Microsoft.Office.Interop.Visio.Page.DrawOval. Кроме того, можно извлекать образцы из наборов элементов и размещать фигуры на странице с помощью метода Microsoft.Office.Interop.Visio.Page.Drop или Microsoft.Office.Interop.Visio.Page.DropMany.  
  
## Работа с документацией по объектной модели Visio  
 Полные сведения об объектной модели Visio см. в справочнике по объектной модели Visio VBA. В справочных документах по объектной модели VBA объектная модель Visio описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в разделе [Справочник по объектной модели Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и членам основной сборки взаимодействия Visio. Например, объект Document в справочнике по объектной модели VBA соответствует типу Microsoft.Office.Interop.Visio.Document в основной сборке взаимодействия Visio. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C\#, если требуется использовать их в проекте надстройки Visio VSTO, создаваемом с помощью Visual Studio.  
  
> [!NOTE]  
>  В настоящее время справочная документация по основной сборке взаимодействия Visio отсутствует.  
  
 Соответствующие примеры кода и сведения о дополнительных средствах для создания решений Visio см. в разделе [Пакет SDK для Visio 2010](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### Дополнительные типы в основных сборках взаимодействия  
 В основных сборках взаимодействия можно найти типы, которые не видны для VBA из\-за различий в реализации. VBA предоставляет представление объектной модели Visio, включающее только те объекты и члены, которые можно использовать напрямую. Основные сборки взаимодействия предоставляют такую же объектную модель, но они также содержат другие интерфейсы, классы и члены, которые преобразуют объекты объектной модели COM в управляемый код. Эти дополнительные элементы не предназначены для непосредственного использования в коде.  
  
 Дополнительные сведения см. в разделах [Общие сведения о классах и интерфейсах в основных сборках взаимодействия Office](http://go.microsoft.com/fwlink/?LinkId=189592) и [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
## См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Работа с документами Visio](../vsto/working-with-visio-documents.md)   
 [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)  
  
  