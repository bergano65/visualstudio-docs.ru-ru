---
title: Приступить к программированию надстроек VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7249c3971c8008f70b9e5add79adddde17fe6a82
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
---
# <a name="get-started-programming-vsto-add-ins"></a>Приступить к программированию надстроек VSTO
  Надстройки VSTO можно использовать для автоматизации приложений Microsoft Office, расширения функциональных возможностей приложения и настройки пользовательского интерфейса приложения. Сведения о сравнении надстроек VSTO для других типов решений Office, можно создать с помощью Visual Studio см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>Создание проектов надстроек VSTO  
 Создание проектов надстроек VSTO с помощью одного из надстройки VSTO шаблонов проектов в **новый проект** диалоговое окно. Эти шаблоны включают в себя необходимые ссылки на сборки и файлы проекта. Visual Studio предоставляет шаблоны проектов надстроек VSTO для большинства приложений Office.  
  
 Дополнительные сведения о создании проекта надстройки VSTO см. в разделе [как: проектов Office, создайте в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).  
  
## <a name="develop-vsto-add-in-projects"></a>Разработка проектов надстроек VSTO  
 При создании проекта надстройки VSTO Visual Studio автоматически создает *ThisAddIn.vb* (в [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) или *ThisAddIn.cs* файл кода (в C#). Этот файл содержит `ThisAddIn` класс, который является основой для надстройки VSTO. Члены этого класса можно использовать для выполнения кода при загрузке или выгрузке надстройки VSTO, при доступе к объектной модели ведущего приложения, а также при расширении функциональных возможностей приложения. Дополнительные сведения см. в разделе [надстроек VSTO программы](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-applications-by-using-the-object-models"></a>Автоматизация приложений с помощью объектных моделей  
 Объектные модели приложений Microsoft Office предоставляют множество типов, которые можно использовать в надстройке VSTO. Эти типы можно использовать для автоматизации приложения. Например, можно программным образом создавать и отправлять сообщение электронной почты в Outlook или можно открыть документ и добавить контент в Word. Дополнительные сведения о способах доступа к объектной модели ведущего приложения в коде см. в разделе [надстроек VSTO программы](../vsto/programming-vsto-add-ins.md).  
  
 Дополнительные сведения об объектных моделях конкретных приложений Microsoft Office см. в следующих статьях:  
  
-   [Общие сведения о модели объектов Excel](../vsto/excel-object-model-overview.md)  
  
-   [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)  
  
-   [Общие сведения о модели объектов Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Решения InfoPath](../vsto/infopath-solutions.md)  
  
-   [Решения PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Решения Project](../vsto/project-solutions.md)  
  
-   [Общие сведения о модели объектов Visio](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>Настройка пользовательского интерфейса приложений  
 Существует несколько способов настройки пользовательского интерфейса ведущего приложения с помощью надстройки VSTO.  
  
-   Для Excel и Word в документы можно добавлять управляемые элементы управления. Дополнительные сведения см. в разделе [документов расширить Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Можно настроить ленту, если ее поддерживает приложение. Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  
  
-   Можно создать настраиваемую область задач, если ее поддерживает приложение. Дополнительные сведения см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md).  
  
-   Для Outlook можно создать пользовательскую область формы. Дополнительные сведения см. в разделе [областей форм Outlook создайте](../vsto/creating-outlook-form-regions.md).  
  
-   Для всех приложений Microsoft Office формы Windows Forms можно отображать в надстройке VSTO.  
  
 Дополнительные сведения о настройке пользовательского интерфейса Microsoft Office см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о создании надстроек VSTO см. в следующих пошаговых руководствах.  
  
-   [Пошаговое руководство: Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Пошаговое руководство: Создание вашей первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Пошаговое руководство: Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Пошаговое руководство: Создание вашей первой надстройки VSTO для проекта](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Пошаговое руководство: Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 В этих пошаговых руководствах рассматриваются средства разработки решений на базе Office в Visual Studio и модель программирования для надстроек VSTO.  
  
 Список разделов с пошаговыми руководствами для некоторых общих задач в проектах Office см. в разделе [общие задачи программирования Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>См. также  
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Приступая к работе &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Напишите код в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)  
  
  