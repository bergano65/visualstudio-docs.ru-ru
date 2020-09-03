---
title: Основные сведения о типе проекта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706382"
---
# <a name="project-type-essentials"></a>Основные компоненты типа проекта
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] включает несколько типов проектов для таких языков, как [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] или [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] также позволяет создавать собственные типы проектов.

 Если вы просто хотите добавить пользовательские команды, редакторы или окна инструментов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , это можно сделать, не создавая новый тип проекта. Дополнительные сведения см. в следующих разделах:

- [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md)

- [Расширение и настройка окон инструментов](../../extensibility/extending-and-customizing-tool-windows.md)

  Аналогично, если необходимо настроить поведение предоставляемых [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] типов проектов и, это можно сделать с помощью подтипов проекта. Дополнительные сведения см. в разделе [Project подтипы](../../extensibility/internals/project-subtypes.md).

  Необходимо создать новый тип проекта для проектов, которые основаны на языке, отличном от [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] , и, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Если требуется поддержка одного или нескольких из следующих элементов:

- Сборка

- Развертывание

- Несколько конфигураций

- Система управления версиями

- Отладка

- Элементы проекта в обозреватель решений

- Диалоговые окна " **Открыть проект** " или " **создать проект** "

- Вложенность проекта

- Дополнительные сведения о возможностях типов проектов см. в следующих статьях:

- Типы проектов — это объекты в пакете VSPackage, реализующие набор интерфейсов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Если вы используете C# для разработки типа проекта, классы проектов платформы управляемых пакетов реализуют необходимые интерфейсы и позволяют наследовать эту реализацию. Дополнительные сведения см. в разделе [использование платформы управляемых пакетов для реализации типа проекта (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Для разработчиков на C++ классы в библиотеке Хиерутил работают аналогичным образом. Дополнительные сведения см. [в разделе не в сборке. Использование классов проектов HierUtil7 для реализации типа проекта (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Типы проектов могут поддерживать данные, отличные от обычных файлов исходного кода, которые создаются в сборке exe или DLL. Например, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекты баз данных содержат ссылки на файлы скриптов и запросов, хранящиеся на диске, и добавляют команды для **Обозреватель решений** для выполнения скриптов и запросов к базе данных, но проекты не поддерживают поведение сборки. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).

- Тип проекта не обязательно должен использовать файлы. Например, тип проекта может хранить все его данные в базе данных. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Типы проектов дают полный контроль над тем, как они сохраняют данные для проектов и элементов проектов. Дополнительные сведения см. в разделе [решения по проектированию типов проектов](../../extensibility/internals/project-type-design-decisions.md).

- Типы проектов должны предоставлять *фабрику проектов*, которая представляет собой объект, создающий экземпляр типа проекта каждый раз, когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо открыть или создать проект, основанный на этом типе проекта. Дополнительные сведения см. в разделе [Создание экземпляров проекта с помощью фабрик проекта](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Типы проектов должны предоставлять шаблоны для проектов и элементов проектов. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует шаблоны, когда пользователи создают новые проекты и добавляют новые элементы в существующие проекты. Дополнительные сведения см. в разделе [Добавление шаблонов проектов и элементов проектов](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Типы проектов могут поддерживать несколько конфигураций, таких как отладка и выпуск. Пользователи могут изменять различные конфигурации проекта с помощью предоставленных страниц свойств. Дополнительные сведения см. в разделе [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>См. также раздел
- [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)
