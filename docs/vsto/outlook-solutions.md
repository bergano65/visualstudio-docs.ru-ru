---
title: "Решения Outlook | Microsoft Docs"
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
  - "решения [разработка решений Office в Visual Studio], Outlook"
  - "проекты Office [разработка решений Office в Visual Studio], Outlook"
  - "решения Office [разработка решений Office в Visual Studio], Outlook"
  - "шаблоны [разработка решений Office в Visual Studio], Outlook"
  - "проекты [разработка решений Office в Visual Studio], Outlook"
  - "Outlook [разработка решений Office в Visual Studio]"
  - "электронная почта [разработка решений Office в Visual Studio], решения Outlook"
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Решения Outlook
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Outlook. Надстройки VSTO можно использовать для автоматизации Outlook, расширения его функциональных возможностей и настройки пользовательского интерфейса Outlook. Дополнительные сведения о надстройках VSTO см. в разделе [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Создание проекта надстройки Outlook VSTO  
 Проекты Outlook создаются с помощью шаблона проекта **Надстройки Outlook** в диалоговом окне **Создание проекта**. Этот шаблон включает в себя необходимые ссылки на сборки и файлы проекта.  
  
 Дополнительные сведения о создании проекта надстройки VSTO см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).  
  
## Модель программирования надстроек VSTO для Outlook  
 При создании проекта надстройки VSTO для Outlook Visual Studio создает класс с именем `ThisAddIn`, который служит базой для вашего решения. Этот класс служит отправной точкой для написания собственного кода, а также предоставляет объектную модель Outlook для надстройки.  
  
 Дополнительные сведения о классе `ThisAddIn` и других возможностях, которые можно использовать в надстройке VSTO, см. в разделе [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
## Автоматизация Outlook с помощью объектной модели Outlook  
 Объектная модель Outlook предоставляет различные типы, которые можно использовать для автоматизации Outlook. С их помощью можно написать код для выполнения распространенных задач:  
  
-   программное создание и отправка электронных сообщений;  
  
-   отправка новых приглашений на собрание;  
  
-   поиск элементов в папках Outlook.  
  
 Для получения дополнительной информации см. [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md).  
  
## Настройка пользовательского интерфейса приложения Outlook  
  
|Задача|Дополнительные сведения|  
|------------|-----------------------------|  
|Добавление пользовательских вкладок на ленту инспектора Outlook.|[Обзор ленты](../vsto/ribbon-overview.md)|  
|Добавление настраиваемых групп на встроенную вкладку инспектора Outlook.|[Практическое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)|  
|Добавление настраиваемой области задач, которая отображается в окне инспектора Outlook.|[Настраиваемые области задач](../vsto/custom-task-panes.md).|  
|Добавление области формы, расширяющей или заменяющей существующие формы Outlook.|[Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Дополнительные сведения о настройке пользовательского интерфейса Outlook и других приложений Microsoft Office см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
## Связанные разделы  
  
|Заголовок|Описание|  
|---------------|--------------|  
|[Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)|Обзор объектов, предоставляемых объектной моделью Outlook.|  
|[Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)|Описание средств Visual Studio, которые упрощают процесс проектирования, разработки и отладки областей формы.|  
|[Пошаговое руководство. Создание первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Здесь показано, как создать надстройку VSTO для Microsoft Office Outlook.|  
|[Outlook 2010 при разработке решений для Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Раздел библиотеки MSDN, содержащий статьи и справочную документацию по разработке решений для Outlook \(не только с помощью Visual Studio\).|  
  
  