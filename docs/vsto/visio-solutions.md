---
title: "Решения Visio | Microsoft Docs"
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
  - "проекты Office [разработка решений Office в Visual Studio], Visio"
  - "решения [разработка решений Office в Visual Studio], Visio"
  - "Visio [разработка решений Office в Visual Studio]"
  - "шаблоны [разработка решений Office в Visual Studio], Visio"
  - "проекты [разработка решений Office в Visual Studio], Visio"
  - "решения Office [разработка решений Office в Visual Studio], Visio"
ms.assetid: c52948c6-6891-43ec-93ff-c54c74ec6016
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Решения Visio
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Visio. Надстройки VSTO можно использовать для автоматизации Visio, расширения функциональных возможностей этого продукта и настройки его пользовательского интерфейса.  
  
 Дополнительные сведения о надстройках VSTO см. в разделах [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием для Microsoft Office, изучите раздел [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для Visio 2010. Дополнительные сведения см. в разделе [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
## Автоматизация Visio с помощью объектной модели Visio  
 Объектная модель Visio предоставляет различные классы, которые можно использовать для автоматизации Visio с целью создания диаграмм для организационных диаграмм, блок\-схем, временных шкал проекта, сетевых диаграмм, пространств Office и проч. Интерфейс API позволяет написать код для выполнения общих задач.  
  
-   Конструирование и размещение фигур и текста в диаграммах.  
  
-   Управление поведением фигур с учетом бизнес\-логики и данных, вводимых пользователем.  
  
-   Управление отображением диаграмм, например панорамированием и масштабированием.  
  
-   Настройка пользовательского интерфейса приложения.  
  
-   Импортируйте внешние данные в Visio, свяжите их с фигурами и отобразите в графическом виде на странице.  
  
 Пошаговые инструкции и примеры кода по использованию объектной модели Visio для работы с документами и фигурами см. в разделах [Работа с документами Visio](../vsto/working-with-visio-documents.md) и [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md).  
  
 Для доступа к объектной модели Visio из надстройки VSTO используйте поле `Application` класса `ThisAddIn` в своем проекте. Поле `Application` возвращает объект Microsoft.Office.Interop.Visio.Application, представляющий текущий экземпляр Visio. Для получения дополнительной информации см. [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
 При вызове объектной модели Visio используются типы, предоставляемые в основной сборке взаимодействия \(PIA\) для Visio. Основная сборка взаимодействия выступает в качестве моста между управляемым кодом в надстройке VSTO и объектной моделью COM в Visio. Все типы в основной сборке взаимодействия Visio определены в пространстве имен Microsoft.Office.Interop.Visio. Дополнительные сведения об основных сборках взаимодействия см. в разделах [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) и [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
## Общие сведения об объектной модели Visio  
 Обзор объектной модели Visio см. в разделе [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md), который содержит ссылки на справочник по объектной модели Visio и пакеты SDK.  
  
## Настройка пользовательского интерфейса Visio  
 Пользовательский интерфейс Visio имеет следующие возможности настройки.  
  
|Задача|Дополнительные сведения|  
|------------|-----------------------------|  
|Настройка ленты.|[Обзор ленты](../vsto/ribbon-overview.md)|  
  
 Сведения о настройке пользовательского интерфейса Visio см. в справочной документации по VBA для класса [Visio.UIObject](HV10077129).  
  
## См. также  
 [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Visio 2010 при разработке решений для Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  