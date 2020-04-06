---
title: Основные элементы проекта (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706382"
---
# <a name="project-type-essentials"></a>Основные компоненты типа проекта
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]включает в себя несколько [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]типов проектов для языков, таких как или . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]также позволяет создавать собственные типы проектов.

 Если вы просто хотите добавить пользовательские команды, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]редакторы или окна инструментов, вы можете сделать это без создания нового типа проекта. Дополнительные сведения см. в следующих разделах:

- [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md)

- [Расширение и настройка окон инструментов](../../extensibility/extending-and-customizing-tool-windows.md)

  Аналогичным образом, если вы хотите настроить поведение [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] поставляемых и типов проектов, вы можете сделать это с помощью подтипов проекта. Для получения дополнительной информации [см.](../../extensibility/internals/project-subtypes.md)

  Необходимо создать новый тип проекта для проектов, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] основанных на языке, отличном от языка, и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] если вы хотите поддержать один или несколько из следующих:

- Построение

- Развертывание

- Несколько конфигураций

- Система управления версиями

- Отладка

- Элементы проекта в Исследователе решений

- Диалог **«Открытый проект»** или **«Новый проект»**

- Проект гнездования

- Для получения дополнительной информации о возможностях типов проектов см.

- Типы проектов являются объектами в VSPackage, которые реализуют набор интерфейсов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ожидает. Если вы используете C-класс для разработки типа проекта, классы проекта Managed Package Framework реализуют необходимые для вас интерфейсы и позволяют унаследовать эту реализацию. Для получения дополнительной информации [см.](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- Для разработчиков СЗ классы в библиотеке HierUtil работают аналогичным образом. Для получения дополнительной информации [см. Не в сборке: Использование классов проекта HierUtil7 для реализации типа проекта (СЗ)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Типы проектов могут поддерживать данные, отличные от типичных файлов исходного кода, которые встраивались в сборку .exe или .dll. Например, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекты баз данных содержат ссылки на файлы скриптов и запросов, хранящиеся на диске, и добавляют команды **в Solution Explorer** для выполнения сценариев и запросов в отношении базы данных, но проекты не поддерживают поведение сборки. Для получения дополнительной информации [см.](../../extensibility/internals/opening-and-saving-project-items.md)

- Тип проекта не должен использовать файлы вообще. Например, тип проекта может хранить все свои данные в базе данных. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]дает типам проектов полный контроль над тем, как они сохраняются данные для проектов и элементов проекта. Для получения дополнительной [Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md)информации см.

- Типы проектов должны предоставлять *фабрику проектов,* которая является объектом, который создает экземпляр типа проекта всякий раз, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] когда ему сказано открыть или создать проект, основанный на этом типе проекта. Для получения дополнительной информации [см.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

- Типы проектов должны поставлять шаблоны для проектов и элементов проекта. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]использует шаблоны, когда пользователи создают новые проекты и добавляют новые элементы в существующие проекты. Для получения дополнительной [информации см.](../../extensibility/internals/adding-project-and-project-item-templates.md)

- Типы проектов могут поддерживать несколько конфигураций, таких как debug и Release. Пользователи могут изменять различные конфигурации проекта, используя страницы свойств, которые вы поставляете. Для получения дополнительной информации [см.](../../extensibility/internals/managing-configuration-options.md)

## <a name="see-also"></a>См. также
- [Развертывание типов проектов](../../extensibility/internals/deploying-project-types.md)
