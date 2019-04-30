---
title: Основные компоненты типа проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16031cbe5152c49c56b4c151e85b01ecf2f91a21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859579"
---
# <a name="project-type-essentials"></a>Основные компоненты типа проекта
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] содержит несколько типов проектов, для языков, таких как [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] или [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] также позволяет создавать собственные типы проектов.

 Если требуется добавить пользовательские команды, редакторы или окна инструментов, чтобы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], это можно сделать без создания нового типа проекта. Дополнительные сведения см. в следующих разделах:

- [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md)

- [Расширение и настройка окон инструментов](../../extensibility/extending-and-customizing-tool-windows.md)

  Аналогично Если вы хотите настроить поведение предоставленного [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] типов проектов, можно сделать это с помощью подтипов проекта. Дополнительные сведения см. в разделе [подтипов проекта](../../extensibility/internals/project-subtypes.md).

  Необходимо создать новый тип проекта для проектов, которые основаны на языке, отличное от [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Если вы хотите поддерживать одну или несколько из следующих:

- Построить

- Развертывание

- Несколько конфигураций

- Система управления версиями

- Отладка

- Элементы проекта в обозревателе решений

- **Открытие проекта** или **новый проект** диалоговые окна

- Вложенность проекта

- Дополнительные сведения о возможностях типов проектов см. в следующих:

- Типы проектов, представляют собой объекты VSPackage, реализовать набор интерфейсов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ожидает. При использовании C# для разработки тип проекта, проект классы Managed Package Framework реализуют интерфейсы, необходимые для вас и позволяют наследовать эту реализацию. Дополнительные сведения см. в разделе [с помощью Managed Package Framework для реализации типа проекта (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Для разработчиков C++ классы в библиотеке HierUtil работать аналогичным образом. Дополнительные сведения см. в разделе [не в сборке: Использование HierUtil7 проект классов для реализации типа проекта (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Типы проектов могут поддерживать использование данных, отличных от файлов обычно исходного кода, встраиваемый в сборку .exe или .dll. Например [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекты баз данных содержат ссылки на файлы скриптов и запросов, хранящихся на диске и добавлять команды для **обозревателе решений** для выполнения скриптов и запросов к базе данных, но проекты не поддерживают реализовать поведение. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).

- Тип проекта не использовать файлы вообще. Например тип проекта может хранить все его данные в базе данных. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Предоставляет типы проектов полный контроль над каким образом они сохраняются данные для проектов и элементов проектов. Дополнительные сведения см. в разделе [проектные решения проекта](../../extensibility/internals/project-type-design-decisions.md).

- Необходимо указать типы проектов *фабрики проектов*, который является объектом, который создает экземпляр проекта введите каждый раз, когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сообщается, чтобы открыть или создать проект, основанный на данный тип проекта. Дополнительные сведения см. в разделе [создание экземпляров с помощью проекта фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Типы проектов, необходимо указать шаблоны проектов и элементов проекта. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует шаблоны, когда пользователям создавать новые проекты и добавлять новые элементы в существующие проекты. Дополнительные сведения см. в разделе [добавление проектов и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Типы проектов может поддерживать несколько конфигураций, например отладки и выпуска. Пользователи могут изменять различные конфигурации проекта с помощью страниц свойств, которые вы указали. Дополнительные сведения см. в разделе [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>См. также
- [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)