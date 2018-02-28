---
title: "Приступая к работе Программирование надстроек VSTO | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: f395ce7fb85d71ed6e8c3f7dfb10726907832873
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="getting-started-programming-vsto-add-ins"></a>Getting Started Programming VSTO Add-ins
  Надстройки VSTO можно использовать для автоматизации приложений Microsoft Office, расширения функциональных возможностей приложения и настройки пользовательского интерфейса приложения. Сведения о сравнении надстроек VSTO для других типов решений Office, можно создать с помощью Visual Studio см. в разделе [Общие сведения о разработке решений Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="creating-vsto-add-in-projects"></a>Создание проектов надстроек VSTO  
 Создание проектов надстроек VSTO с помощью одного из надстройки VSTO шаблонов проектов в **новый проект** диалоговое окно. Эти шаблоны включают в себя необходимые ссылки на сборки и файлы проекта. Visual Studio предоставляет шаблоны проектов надстроек VSTO для большинства приложений Office.  
  
 Дополнительные сведения о создании проекта надстройки VSTO см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).  
  
## <a name="developing-vsto-add-in-projects"></a>Разработка проектов надстроек VSTO  
 При создании проекта надстройки VSTO Visual Studio автоматически создает ThisAddIn.vb (в [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) или в файле кода ThisAddIn.cs (в C#). Этот файл содержит `ThisAddIn` класс, который является основой для надстройки VSTO. Члены этого класса можно использовать для выполнения кода при загрузке или выгрузке надстройки VSTO, при доступе к объектной модели ведущего приложения, а также при расширении функциональных возможностей приложения. Для получения дополнительной информации см. [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-applications-by-using-the-object-models"></a>Автоматизация приложений с помощью объектных моделей  
 Объектные модели приложений Microsoft Office предоставляют множество типов, которые можно использовать в надстройке VSTO. Эти типы можно использовать для автоматизации приложения. Например, можно программным образом создавать и отправлять сообщение электронной почты в Outlook или можно открыть документ и добавить контент в Word. Дополнительные сведения о способах доступа к объектной модели ведущего приложения в коде см. в разделе [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Дополнительные сведения об объектных моделях конкретных приложений Microsoft Office см. в следующих статьях:  
  
-   [Excel Object Model Overview](../vsto/excel-object-model-overview.md)  
  
-   [Word Object Model Overview](../vsto/word-object-model-overview.md)  
  
-   [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)  
  
-   [Решения InfoPath](../vsto/infopath-solutions.md)  
  
-   [Решения PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Решения проектов](../vsto/project-solutions.md)  
  
-   [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customizing-the-user-interface-of-applications"></a>Настройка пользовательского интерфейса приложений  
 Существует несколько способов настройки пользовательского интерфейса ведущего приложения с помощью надстройки VSTO.  
  
-   Для Excel и Word в документы можно добавлять управляемые элементы управления. Для получения дополнительной информации см. [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Можно настроить ленту, если ее поддерживает приложение. Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  
  
-   Можно создать настраиваемую область задач, если ее поддерживает приложение. Дополнительные сведения см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md).  
  
-   Для Outlook можно создать пользовательскую область формы. Дополнительные сведения см. в разделе [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
-   Для всех приложений Microsoft Office формы Windows Forms можно отображать в надстройке VSTO.  
  
 Дополнительные сведения о настройке пользовательского интерфейса Microsoft Office см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о создании надстроек VSTO см. в следующих пошаговых руководствах.  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Пошаговое руководство. Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 В этих пошаговых руководствах рассматриваются средства разработки решений на базе Office в Visual Studio и модель программирования для надстроек VSTO.  
  
 Список разделов с пошаговыми руководствами для некоторых общих задач в проектах Office см. в разделе [общие задачи программирования Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>См. также  
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Приступая к работе &#40; разработка решений Office в Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  