---
title: 'Контрольный список: Создание новых типов проектов (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709753"
---
# <a name="checklist-create-new-project-types"></a>Контрольный список: Создание новых типов проектов
Для создания нового типа проекта необходимо выполнить несколько задач. Следующий контрольный список содержит руководство по этим задачам:

1. Дизайн функциональности для нового типа проекта. Для получения дополнительной [Project type design decisions](../../extensibility/internals/project-type-design-decisions.md)информации см.

2. Определите, какие редакторы используются для кода и других элементов проекта. Вы можете использовать основные или стандартные редакторы, или вы можете создавать и использовать конкретные редакторы проекта. Для получения дополнительной информации [см. Создать пользовательские редакторы и дизайнеры](../../extensibility/creating-custom-editors-and-designers.md) и [Как: Открыть проект конкретных редакторов](../../extensibility/how-to-open-project-specific-editors.md).

3. Определите уровень участия элементов проекта в **классе View** и **Object Browser.** Для получения дополнительной информации смотрите [инструменты просмотра символов поддержки.](../../extensibility/internals/supporting-symbol-browsing-tools.md)

4. Получение новых классов на основе проектных решений, которые вы сделали ранее для элементов проекта и проекта.

5. Напишите код для следующих компонентов типа проекта:

    - Проект завода, для управления созданием новых проектов и открытием существующих проектов. Для получения дополнительной информации [см. Создать экземпляры проектов с помощью проектных фабрик.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

    - Иерархия проекта и обработка команд. Для получения дополнительной информации [см. Используйте классы проектов HierUtil7 для реализации типа проекта (СЗ)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Элементы модели проекта,](../../extensibility/internals/elements-of-a-project-model.md) [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)и [MenuCommands против OleMenuCommands.](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)

    - Управление элементами проекта, включая добавление проекта в диалоговую коробку **Нового проекта.** Для получения дополнительной информации [Register project and item templates](../../extensibility/internals/registering-project-and-item-templates.md)см. [Add project and project item templates](../../extensibility/internals/adding-project-and-project-item-templates.md)

    - Сохранение состояния проекта и отдельных элементов. Для получения дополнительной информации [см.](../../extensibility/internals/opening-and-saving-project-items.md) Для сохранения информации о решении [см.](../../extensibility/internals/solutions-overview.md)

    - Независят от конфигурации свойства для отображения в окне Свойств. Для получения дополнительной информации [см.](../../extensibility/internals/extending-properties.md)

    - Свойства конфигурации проекта, реализованные на страницах свойств, отображаются зависящими от конфигурации свойствами. Для получения дополнительной информации [см.](../../extensibility/internals/managing-configuration-options.md)

    - Перечисление выходов для развертывания. Для получения дополнительной информации [см.](../../extensibility/internals/project-configuration-for-output.md)

    - Услуги по запуску проекта. Для получения дополнительной информации [Project model core components](../../extensibility/internals/project-model-core-components.md)см. [Elements of a project model](../../extensibility/internals/elements-of-a-project-model.md)

    - Объекты, или классы, полученные из, `IDispatch`доступны для автоматизации.

    - Таблица команд XML *(.vsct*) файлы. Для получения дополнительной информации смотрите [файлы командной таблицы Visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

6. Проверьте, отладите и запустите тип проекта.

7. Отображение проекта во вкладке **Project** `VARIANT_TRUE` в диалоговом окне добавления `VSHPROPID_ShowProjInSolutionPage` **ссылки,** установив значение для. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Создайте файл Microsoft Installer *(.msi*) для установки VSPackages. Для получения дополнительной информации смотрите [Установить VSPackages с установкой Windows,](../../extensibility/internals/installing-vspackages-with-windows-installer.md) [зарегистрировать тип проекта](../../extensibility/internals/registering-a-project-type.md)и [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>См. также
- [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Когда создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)
- [Создание типов проектов](../../extensibility/internals/creating-project-types.md)
