---
title: "Решения InfoPath"
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
  - "решения [разработка решений Office в Visual Studio], InfoPath"
  - "шаблоны [разработка решений Office в Visual Studio], InfoPath"
  - "InfoPath [разработка решений Office в Visual Studio]"
  - "разработка решений Office в Visual Studio, решения InfoPath"
  - "проекты [разработка решений Office в Visual Studio], InfoPath"
  - "решения Office [разработка решений Office в Visual Studio], InfoPath"
  - "проекты Office [разработка решений Office в Visual Studio], InfoPath"
ms.assetid: 20ac6bee-b17f-4217-9f78-11304a11236a
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Решения InfoPath
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office InfoPath 2013 и InfoPath 2010. В Office 2016 InfoPath отсутствует.  
  
> [!NOTE]  
>  Даже если установлен Office 2016, вы по\-прежнему можете создавать надстройки VSTO для InfoPath. Просто установите InfoPath 2013 или Office 2013 параллельно с Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
 Надстройки VSTO для InfoPath похожи на надстройки VSTO для других приложений Microsoft Office. Решения такого типа содержат сборку, которую загружает приложение. Конечные пользователи могут получать доступ к функциям этой сборки, независимо от того, какая форма или шаблон формы открыт. Дополнительные сведения о надстройках VSTO см. в разделах [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 не содержит проекты шаблонов форм InfoPath, которые присутствовали в предыдущих версиях Visual Studio. Visual Studio 2015 также нельзя использовать для открытия или изменения проекта шаблонов форм InfoPath, который был создан в предыдущей версии Visual Studio. Однако проект шаблонов форм InfoPath можно открыть и изменить с помощью набора средств Visual Studio Tools для работы с приложениями. Дополнительные сведения см. в статье [Работа с проектами VSTO 2008 в InfoPath 2010](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## Автоматизация InfoPath с помощью надстройки  
 Чтобы получить доступ к объектной модели InfoPath из надстройки VSTO Office, созданной с помощью средств разработки решений на базе Office в Visual Studio, используйте поле `Application` класса `ThisAddIn` в своем проекте. Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.InfoPath.Application>, представляющий текущий экземпляр InfoPath. Дополнительные сведения см. в разделе [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
 При вызове объектной модели InfoPath из надстройки VSTO вы используете типы, предоставляемые основной сборкой взаимодействия для InfoPath. Основная сборка взаимодействия представляет собой мост между управляемым кодом в надстройке VSTO и объектной моделью COM в InfoPath. Все типы в основной сборке взаимодействия InfoPath определены в пространстве имен <xref:Microsoft.Office.Interop.InfoPath>. Дополнительные сведения об основной сборке взаимодействия InfoPath см. в статье [Об основной сборке взаимодействия Microsoft Office InfoPath](http://msdn.microsoft.com/ru-ru/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Дополнительные сведения об основных сборках взаимодействия в целом см. в разделах [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) и [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
## Настройка пользовательского интерфейса для InfoPath с помощью надстройки  
 При создании надстройки VSTO для InfoPath есть несколько вариантов настройки пользовательского интерфейса. Некоторые из них указаны в следующей таблице.  
  
|Задача|Дополнительные сведения|  
|------------|-----------------------------|  
|Создание настраиваемой области задач.|[Настраиваемые области задач](../vsto/custom-task-panes.md)|  
|Добавление настраиваемых вкладок на ленту в InfoPath.|[Настройка ленты для InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Дополнительные сведения о настройке пользовательского интерфейса InfoPath и других приложений Microsoft Office см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
## См. также  
 [Сведения об основной сборке взаимодействия Microsoft Office InfoPath](http://msdn.microsoft.com/ru-ru/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [InfoPath 2010 при разработке решений для Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  