---
title: "Решения Project"
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
  - "проекты [разработка решений Office в Visual Studio], Project"
  - "решения Office [разработка решений Office в Visual Studio], Project"
  - "Project [разработка решений Office в Visual Studio"
  - "шаблоны [разработка решений Office в Visual Studio], Project"
  - "проекты Office [разработка решений Office в Visual Studio], Project"
  - "решения [разработка решений Office в Visual Studio], Project"
ms.assetid: 4ce92269-eb6d-44aa-bee3-6d38ec9995f9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Решения Project
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Project. Надстройки VSTO можно использовать для автоматизации Project, расширения функциональных возможностей этого продукта и настройки его пользовательского интерфейса.  
  
 Дополнительные сведения о надстройках VSTO см. в разделах [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием для Microsoft Office, изучите раздел [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
## Автоматизация Project с помощью объектной модели Project  
 Объектная модель Project предоставляет различные типы, которые можно использовать для автоматизации Project. Эти типы позволяют создавать код для выполнения общих задач, таких как программное создание и изменение задач в проекте.  
  
 Для доступа к объектной модели Project из надстройки VSTO используйте поле `Application` класса `ThisAddIn` в своем проекте. Поле `Application` возвращает объект Microsoft.Office.Interop.MsProject.Application , представляющий текущий экземпляр Project. Для получения дополнительной информации см. [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
 При вызове объектной модели Project используются типы, предоставляемые в основной сборке взаимодействия для Project. Основная сборка взаимодействия представляет собой мост между управляемым кодом в надстройке VSTO и объектной моделью COM в Project. Все типы в основной сборке взаимодействия Project определены в пространстве имен Microsoft.Office.Interop.MSProject. Дополнительные сведения об основных сборках взаимодействия см. в разделах [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) и [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
## Использование документации по объектной модели Project  
 Полные сведения об объектной модели Project см. в справочнике по объектной модели Project VBA. В справочных документах по объектной модели VBA объектная модель Project описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в разделе [Справочник по объектной модели Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и членам основной сборки взаимодействия Project. Например, объект Calendar в справочнике по объектной модели VBA соответствует типу Microsoft.Office.Interop.MSProject.Calendar в основной сборке взаимодействия Project. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C\#, если требуется использовать их в проекте надстройки VSTO для Project, создаваемом с помощью Visual Studio.  
  
> [!NOTE]  
>  В настоящее время справочная документация по основной сборке взаимодействия Project отсутствует.  
  
### Типы инфраструктуры в основной сборке взаимодействия Project  
 При написании кода, использующего основную сборку взаимодействия Project, можно заметить, что многие типы не описаны в справочнике по VBA. Эти дополнительные типы, используемые для преобразования объектов в объектной модели COM Project в управляемый код, не предназначены для непосредственного использования в коде.  
  
 Дополнительные сведения см. в разделе [Общие сведения о классах и интерфейсах в основных сборках взаимодействия Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## Настройка пользовательского интерфейса Project  
 Пользовательский интерфейс Project можно настраивать следующими способами.  
  
|Задача|Дополнительные сведения|  
|------------|-----------------------------|  
|Добавление настраиваемых вкладок на ленту в Project.|[Обзор ленты](../vsto/ribbon-overview.md)|  
  
 Дополнительные сведения о настройке пользовательского интерфейса Project и других приложений Microsoft Office см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
## См. также  
 [Пошаговое руководство. Создание первой надстройки VSTO для Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Project 2010 и Project Server 2010 при разработке решений Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  