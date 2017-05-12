---
title: "Приступая к программированию надстроек VSTO"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.Outlook"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "надстройки [разработка решений Office в Visual Studio], начало работы"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], начало работы"
ms.assetid: 9ac1e6ea-9511-4633-80f9-dc7641f22b63
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Приступая к программированию надстроек VSTO
  Надстройки VSTO можно использовать для автоматизации приложений Microsoft Office, расширения функциональных возможностей приложения и настройки пользовательского интерфейса приложения.  Сведения о сравнении надстроек VSTO с другими типами решений Office, которые можно создавать с помощью Visual Studio, см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Создание проектов надстроек VSTO  
 Для создания проектов надстроек VSTO используйте один из шаблонов проектов надстроек VSTO в диалоговом окне **Создание проекта**.  Эти шаблоны включают в себя необходимые ссылки на сборки и файлы проекта.  Visual Studio предоставляет шаблоны проектов надстроек VSTO для большинства приложений Office.  
  
 Дополнительные сведения о создании проекта надстройки VSTO см. в статье [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Дополнительные сведения о шаблонах проектов см. в статье [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).  
  
## Разработка проектов надстроек VSTO  
 При создании проекта надстройки VSTO среда Visual Studio автоматически создает файл кода ThisAddIn.vb \(в [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) или ThisAddIn.cs \(в C\#\).  Этот файл содержит класс `ThisAddIn`, который является основой для вашей надстройки VSTO.  Члены этого класса можно использовать для выполнения кода при загрузке или выгрузке надстройки VSTO, при доступе к объектной модели ведущего приложения, а также при расширении функциональных возможностей приложения.  Дополнительные сведения см. в статье [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
## Автоматизация приложений с помощью объектных моделей  
 Объектные модели приложений Microsoft Office предоставляют множество типов, которые можно использовать в надстройке VSTO.  Эти типы можно использовать для автоматизации приложения.  Например, можно программным образом создавать и отправлять сообщение электронной почты в Outlook или можно открыть документ и добавить контент в Word.  Дополнительные сведения о доступе к объектной модели ведущего приложения в коде см. в статье [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Дополнительные сведения об объектных моделях конкретных приложений Microsoft Office см. в следующих статьях:  
  
-   [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)  
  
-   [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)  
  
-   [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Решения InfoPath](../vsto/infopath-solutions.md)  
  
-   [Решения PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Решения Project](../vsto/project-solutions.md)  
  
-   [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)  
  
## Настройка пользовательского интерфейса приложений  
 Существует несколько способов настройки пользовательского интерфейса ведущего приложения с помощью надстройки VSTO.  
  
-   Для Excel и Word в документы можно добавлять управляемые элементы управления.  Дополнительные сведения см. в статье [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Можно настроить ленту, если ее поддерживает приложение.  Дополнительные сведения см. в статье [Обзор ленты](../vsto/ribbon-overview.md).  
  
-   Можно создать настраиваемую область задач, если ее поддерживает приложение.  Дополнительные сведения см. в статье [Настраиваемые области задач](../vsto/custom-task-panes.md).  
  
-   Для Outlook можно создать пользовательскую область формы.  Дополнительные сведения см. в статье [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md).  
  
-   Для всех приложений Microsoft Office формы Windows Forms можно отображать в надстройке VSTO.  
  
 Дополнительные сведения о настройке пользовательского интерфейса приложений Microsoft Office см. в статье [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
## Следующие шаги  
 Дополнительные сведения о создании надстроек VSTO см. в следующих пошаговых руководствах.  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 В этих пошаговых руководствах рассматриваются средства разработки решений на базе Office в Visual Studio и модель программирования для надстроек VSTO.  
  
 Список пошаговых руководств для выполнения некоторых типичных задач в проектах Office см. в разделе [Общие задачи программирования Office](../vsto/common-tasks-in-office-programming.md).  
  
## См. также  
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)  
  
  