---
title: "Проект типа Essentials | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 77ac7852a4fe42e69602edcd7e75354b404e315e
ms.lasthandoff: 02/22/2017

---
# <a name="project-type-essentials"></a>Essentials типа проекта
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]содержит несколько типов проектов для языков, таких как [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] или [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]также позволяет создавать собственные типы проектов.  
  
 Если требуется добавить пользовательские команды, редакторы или окна инструментов, чтобы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], это можно сделать без создания нового типа проекта. Дополнительные сведения см. в следующих разделах:  
  
-   [Команды, меню и панелей инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Редактор и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Расширение и настройка окна инструментов](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 Аналогичным образом Если вы хотите настроить поведение предоставленной [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] типов проектов, можно сделать подтипы проектов с помощью. Дополнительные сведения см. в разделе [подтипы проекта](../../extensibility/internals/project-subtypes.md).  
  
 Необходимо создать новый тип проекта для проектов, которые основаны на языке, отличного от [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] чтобы поддерживает один или несколько из следующих действий:  
  
-   Построить  
  
-   Развертывание  
  
-   Несколько конфигураций  
  
-   Система управления версиями  
  
-   Отладка  
  
-   Элементы проекта в обозревателе решений  
  
-   **Открыть проект** или **новый проект** диалоговые окна  
  
-   Вложение проекта  
  
-   Дополнительные сведения о возможностях типов проектов см.  
  
-   Типы проектов — это объекты в VSPackage, реализации набора интерфейсов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ожидает. При использовании C# для разработки тип проекта, классы платформа управляемых пакетов проекта реализовывать интерфейсы, необходимые для вас и позволяют наследовать эту реализацию. Дополнительные сведения см. в разделе [использование платформа управляемых пакетов для реализации типа проекта (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Для разработчиков C++ классы в библиотеке HierUtil работают аналогичным образом. Дополнительные сведения см. в разделе [не в построении: с помощью HierUtil7 проект классы для реализации типа проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Типы проектов может поддерживать данные, отличные от файлы обычно исходного кода, сборки в сборку .exe или .dll. Например [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекты баз данных содержат ссылки на файлы скриптов и запросов, хранятся на диске и команд для **обозревателе решений** для выполнения скриптов и запросов к базе данных, но проекты не поддерживают режим построения. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Тип проекта не использовать файлы вообще. Например тип проекта может хранить все данные в базе данных. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Предоставляет типы проектов контролировать, как они сохраняются данные для проектов и элементов проектов. Дополнительные сведения см. в разделе [решений типа проекта](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Необходимо указать типы проектов *фабрики проекта*, это объект, который создает экземпляр проекта введите всякий раз, когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предлагается откройте или создайте проект, который основан на данный тип проекта. Дополнительные сведения см. в разделе [Создание проекта экземпляров, с помощью проекта фабрик](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Типы проектов необходимо предоставить шаблоны проектов и элементов проектов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]использует шаблоны, когда пользователям создавать новые проекты и добавлять новые элементы в существующие проекты. Дополнительные сведения см. в разделе [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Типы проектов может поддерживать несколько конфигураций, например Debug и Release. Пользователи могут изменять различные конфигурации проекта с помощью страниц свойств, которые предоставляются. Дополнительные сведения см. в разделе [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>См. также  
 [Развертывание типы проектов](../../extensibility/internals/deploying-project-types.md)
