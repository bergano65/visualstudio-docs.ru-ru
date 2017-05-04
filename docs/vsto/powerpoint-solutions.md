---
title: "Решения PowerPoint | Microsoft Docs"
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
  - "решения Office [разработка решений Office в Visual Studio], PowerPoint"
  - "шаблоны [разработка решений Office в Visual Studio], PowerPoint"
  - "решения [разработка решений Office в Visual Studio], PowerPoint"
  - "проекты [разработка решений Office в Visual Studio], PowerPoint"
  - "PowerPoint [разработка решений Office в Visual Studio]"
  - "проекты Office [разработка решений Office в Visual Studio], PowerPoint"
ms.assetid: 02ebad64-9fd3-495f-ab27-4f6206b3d6d2
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Решения PowerPoint
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office PowerPoint. Вы можете использовать надстройки VSTO для автоматизации PowerPoint, расширения и настройки пользовательского интерфейса PowerPoint.  
  
 Дополнительные сведения о надстройках VSTO см. в разделах [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием для Microsoft Office, изучите раздел [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 ![ссылка на видео](../vsto/media/playvideo.png "ссылка на видео") Демонстрационные видеоматериалы см. в разделе [Практическое руководство. Создание надстройки для Microsoft PowerPoint](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## Автоматизация PowerPoint с помощью объектной модели PowerPoint  
 Объектная модель Word предоставляет различные типы, которые можно использовать для автоматизации Word. С их помощью можно написать код для выполнения распространенных задач:  
  
-   программное создание и форматирование презентаций;  
  
-   добавление и удаление слайдов из презентаций;  
  
-   добавление и изменение фигур на слайде.  
  
 Для доступа к объектной модели PowerPoint из надстройки VSTO используйте поле `Application` класса `ThisAddIn` в своем проекте. Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.PowerPoint.Application>, представляющий текущий экземпляр PowerPoint. Дополнительные сведения см. в разделе [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
 При вызове объектной модели PowerPoint используются типы, предоставляемые в основной сборке взаимодействия для PowerPoint. Основная сборка взаимодействия представляет собой мост между управляемым кодом в надстройке VSTO и объектной моделью COM в PowerPoint. Все типы в основной сборке взаимодействия PowerPoint определены в пространстве имен <xref:Microsoft.Office.Interop.PowerPoint>. Дополнительные сведения об основных сборках взаимодействия см. в разделах [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) и [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Работа с документацией по объектной модели PowerPoint  
 Полные сведения об объектной модели PowerPoint см. в справочнике по основной сборке взаимодействия PowerPoint и в справочнике по объектной модели VBA.  
  
### Документация по основной сборке взаимодействия  
 В справочной документации по основной сборке взаимодействия PowerPoint описываются типы основной сборки взаимодействия для PowerPoint. Эта документация доступна на следующей странице: [Справочник по основной сборке взаимодействия PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Дополнительные сведения о структуре основных сборок взаимодействия PowerPoint, включая различия между классами и интерфейсами в основных сборках взаимодействия и порядок реализации событий в этих сборках, см. в разделе [Общие сведения о классах и интерфейсах в основных сборках взаимодействия Office](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### Справочник по объектной модели VBA  
 В справочных документах по объектной модели VBA объектная модель PowerPoint описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в разделе [Справочник по объектной модели PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770).  
  
 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и членам основной сборки взаимодействия PowerPoint. Например, объект Presentation в справочнике по объектной модели VBA соответствует типу <xref:Microsoft.Office.Interop.PowerPoint.Presentation> в основной сборке взаимодействия PowerPoint. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C\#, если требуется использовать его в проекте надстройки VSTO для PowerPoint, создаваемом с помощью Visual Studio.  
  
## Настройка пользовательского интерфейса PowerPoint  
 Пользовательский интерфейс PowerPoint можно изменить следующими способами.  
  
|Задача|Дополнительные сведения|  
|------------|-----------------------------|  
|Создание настраиваемой области задач.|[Настраиваемые области задач](../vsto/custom-task-panes.md)|  
|Добавление настраиваемых вкладок на ленту.|[Обзор ленты](../vsto/ribbon-overview.md)|  
|Добавление настраиваемых групп на встроенную вкладку на ленте.|[Практическое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Дополнительные сведения о настройке пользовательского интерфейса для PowerPoint и других приложений Microsoft Office см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
## См. также  
 [Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 при разработке решений для Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  