---
title: Проект типа Essentials | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aff6cc669d7df46acaa2cbcb129a6b13b7261d9b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134425"
---
# <a name="project-type-essentials"></a>Essentials тип проекта
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] содержит несколько типов проектов для языков, таких как [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] или [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] позволяет также создавать собственные типы проектов.  
  
 Если требуется добавить пользовательские команды, редакторы или окна инструментов, чтобы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], это можно сделать, не создавая новый тип проекта. Дополнительные сведения см. в следующих разделах:  
  
-   [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Расширение и настройка окон инструментов](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 Точно так же если вы хотите настроить поведение предоставленной [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] типы проектов, можно сделать с помощью подтипы проекта. Дополнительные сведения см. в разделе [подтипы проекта](../../extensibility/internals/project-subtypes.md).  
  
 Необходимо создать новый тип проекта для проектов, основанных на язык, отличный от [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] чтобы поддерживает один или несколько из следующих действий:  
  
-   Построить  
  
-   Развертывание  
  
-   Несколько конфигураций  
  
-   Система управления версиями  
  
-   Отладка  
  
-   Элементы проекта в обозревателе решений  
  
-   **Открытие проекта** или **новый проект** диалоговые окна  
  
-   Вложение проекта  
  
-   Дополнительные сведения о возможностях типов проектов см.  
  
-   Типы проектов, представляют собой объекты VSPackage, реализовывать в набор интерфейсов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ожидает. При использовании C# при разработке типа проекта, классы Managed Package Framework проекта реализовать интерфейсы, необходимые для вас и позволяют наследует эту реализацию. Дополнительные сведения см. в разделе [с помощью Managed Package Framework для реализации типа проекта (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Для разработчиков C++ классы в библиотеке HierUtil работать аналогичным образом. Дополнительные сведения см. в разделе [не в сборке: с помощью HierUtil7 проекта классов для реализации типа проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Типы проектов может поддерживать данные, отличные от файлов типичные исходного кода, создающие в сборку .exe или .dll. Например [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекты баз данных содержат ссылки на файлы скриптов и запросов, хранящихся на диске и команд для **обозревателе решений** для выполнения скриптов и запросов к базе данных, но эти проекты не поддерживают реализовать поведение. Дополнительные сведения см. в разделе [открытия и сохранения элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Тип проекта имеет вообще использовать файлы. Например тип проекта может хранить все данные в базе данных. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Предоставляет типы проектов полный контроль над сохранением данных для проектов и элементов проектов. Дополнительные сведения см. в разделе [проектные решения проекта типа](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Необходимо указать типы проектов *фабрики проектов*, являющийся объектом, который создает экземпляр проекта введите каждый раз, когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сообщается, чтобы открыть или создать проект, зависит от типа проекта. Дополнительные сведения см. в разделе [Создание проекта экземпляров, с помощью проекта фабрик](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Типы проектов необходимо указать шаблоны проектов и элементов проектов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует шаблоны при пользователям создание новых проектов и добавления новых элементов к существующим проектам. Дополнительные сведения см. в разделе [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Типы проектов может поддерживать несколько конфигураций, например, Debug и Release. Пользователи могут изменять различные конфигурации проекта с помощью страниц свойств, которые предоставляются. Дополнительные сведения см. в разделе [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>См. также  
 [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)