---
title: Тип функции, доступные по приложений Office и проектов
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4b0c4ea5ec07fec187c5fa377239cdec2ccceb5
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
---
# <a name="features-available-by-office-application-and-project-type"></a>Тип функции, доступные по приложений Office и проектов
  В Visual Studio есть шаблоны проектов нескольких типов, которые поддерживают различные бизнес-сценарии для приложений Microsoft Office, включая следующие типы:  
  
-   Настройки на уровне документа.  
  
-   Надстройки VSTO.  
  
 Не все приложения могут использовать любой тип проекта. Например, проекты уровня документа доступны только для Microsoft Office Word и Microsoft Office Excel. Аналогичным образом, некоторые функции доступны только для проектов или приложений определенных типов. Например, панель действий доступна только в проектах уровня документа, а расширения ленты — только для некоторых приложений. Дополнительные сведения о различных типах проектов см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Шаблоны проектов Office доступны только в некоторых выпусках [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>Типы проектов, доступные для различных приложений Microsoft Office  
 В следующей таблице указаны приложения, которые можно использовать в проекте каждого типа.  
  
|Типы проектов|Приложение Microsoft Office|  
|-------------------|----------------------------------|  
|Настройки уровня документа.|Excel<br /><br /> Слово|  
|Надстройки VSTO|Excel<br /><br /> InfoPath (только InfoPath 2013 и InfoPath 2010).<br /><br /> Outlook - приложение<br /><br /> PowerPoint<br /><br /> Проект<br /><br /> Visio<br /><br /> Слово<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>Функции, доступные в различных типах проектов  
 В следующей таблице показано, какие возможности доступны в каких типах проектов.  
  
|Функция|Типы проектов, предоставляющие функцию|Дополнительные сведения|  
|-------------|--------------------------------------------|---------------------|  
|Панель действий.|Проекты уровня документа.|[Общие сведения о панели действий](../vsto/actions-pane-overview.md)|  
|Развертывание ClickOnce.|Проекты VS и уровня документа.|[Развертывание решения Office](../vsto/deploying-an-office-solution.md)|  
|Настраиваемые области задач.|Проекты надстроек VSTO для следующих приложений:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 и InfoPath 2010 только)<br />-Outlook<br />-PowerPoint<br />-Word|[Настраиваемые области задач](../vsto/custom-task-panes.md)|  
|Пользовательские XML-части.|Проекты уровня документа.<br /><br /> Проекты уровня приложения для следующих приложений:<br /><br /> -Excel<br />-PowerPoint<br />-Word|[Общие сведения о пользовательских частей XML](../vsto/custom-xml-parts-overview.md)|  
|Кэш данных.|Проекты уровня документа.|[Кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md)|  
|Предоставление объекта в надстройке VSTO другим решениям Microsoft Office.|Проекты надстроек VSTO.|[Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|Следующие элементы управления ведущего приложения:<br /><br /> — Создание диаграмм<br />-Элемент управления ListObject<br />-NamedRange<br />-Элементы управления содержимым<br />-Закладки|Проекты уровня документа.<br /><br /> Проекты надстроек VSTO для Word и Excel.|[Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)|  
|Следующие элементы управления ведущего приложения:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|Проекты уровня документа.|[Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)|  
|Развертывание нескольких проектов.|Проекты уровня документа.<br /><br /> Проекты надстроек VSTO.|[Пошаговое руководство: Развертывание нескольких решений Office в одном установщике ClickOnce](http://msdn.microsoft.com/en-us/051223c0-4082-4799-b78b-a4763a9def55)|  
|Области формы Outlook.|Проекты надстроек VSTO для Outlook.|[Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)|  
|Действия, выполняемые после развертывания.|Проекты уровня документа.<br /><br /> Проекты надстроек VSTO.|[Пошаговое руководство: Скопируйте документ на компьютере конечного пользователя после установки с помощью ClickOnce](http://msdn.microsoft.com/en-us/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Настройки ленты.|Проекты уровня документа.<br /><br /> Проекты надстроек VSTO для следующих приложений:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 и InfoPath 2010 только)<br />-Outlook<br />-PowerPoint<br />-Проект<br />-Visio<br />-Word|[Обзор ленты](../vsto/ribbon-overview.md)|  
|Визуальный конструктор документов.|Проекты уровня документа.|[Проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  