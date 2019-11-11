---
title: 'Контрольный список: создание новых типов проектов | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 048f2f61e080230113cd303a202c3819d2c58710
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186627"
---
# <a name="checklist-create-new-project-types"></a>Контрольный список: создание новых типов проектов
Для создания нового типа проекта необходимо выполнить несколько задач. В следующем контрольном списке приведено руководство по этим задачам.

1. Разработайте функциональные возможности нового типа проекта. Дополнительные сведения см. в разделе [решения по проектированию типов проектов](../../extensibility/internals/project-type-design-decisions.md).

2. Определите, какие редакторы используются для кода и других элементов проекта. Можно использовать редакторы Core или Standard или создавать и использовать редакторы для конкретных проектов. Дополнительные сведения см. в статьях [Создание пользовательских редакторов и конструкторов](../../extensibility/creating-custom-editors-and-designers.md) и [инструкции: открытие редакторов для конкретных проектов](../../extensibility/how-to-open-project-specific-editors.md).

3. Определите уровень участия, которые будут иметь элементы проекта в **представление классов** и **обозревателе объектов**. Дополнительные сведения см. в разделе [Поддержка средств просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Создавайте новые классы на основе решений, принятых ранее для проекта и элементов проекта.

5. Напишите код для следующих компонентов типа проекта:

    - Фабрика проектов для управления созданием новых проектов и открытия существующих проектов. Дополнительные сведения см. в статье [Создание экземпляров проектов с помощью фабрик проекта](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Иерархия проектов и обработка команд. Дополнительные сведения см. в статьях [Использование классов проектов HierUtil7 для реализации типа проектаC++()](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [элементов модели проекта](../../extensibility/internals/elements-of-a-project-model.md), [основных компонентов модели проекта](../../extensibility/internals/project-model-core-components.md), а [команды MenuCommand и олеменукоммандс](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

    - Управление элементами проекта, включая добавление проекта в диалоговое окно **Новый проект** . Дополнительные сведения см. в статьях [Добавление шаблонов проектов и элементов проектов](../../extensibility/internals/adding-project-and-project-item-templates.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).

    - Сохраняемость состояния проекта и отдельных элементов. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md). Сведения о сохранении сведений о решении см. в разделе [решения](../../extensibility/internals/solutions-overview.md).

    - Свойства, независимые от конфигурации, которые отображаются в окно свойств. Дополнительные сведения см. в разделе [расширение свойств](../../extensibility/internals/extending-properties.md).

    - Свойства конфигурации проекта, реализованные на страницах свойств, для отображения свойств, зависящих от конфигурации. Дополнительные сведения см. в разделе [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md).

    - Перечисление выходных данных для развертывания. Дополнительные сведения см. в разделе [Конфигурация проекта для выходных данных](../../extensibility/internals/project-configuration-for-output.md).

    - Службы запуска проектов. Дополнительные сведения см. в разделе [элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md) и [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md).

    - Объекты или классы, производные от `IDispatch`, доступны для автоматизации.

    - Файлы таблицы команд XML ( *. vsct*). Дополнительные сведения см. в разделе [файлы командных таблиц Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

6. Тестирование, отладка и запуск типа проекта.

7. Отобразите проект на вкладке **проект** диалогового окна **Добавление ссылки** , задав `VARIANT_TRUE` в качестве значения для `VSHPROPID_ShowProjInSolutionPage`. Дополнительные сведения см. в разделах <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Создайте файл установщика Microsoft (*MSI*) для установки пакетов VSPackage. Дополнительные сведения см. в статьях [Установка пакетов VSPackage с установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md)и [пакетов VSPackage](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>См. также
- [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)
- [Создание типов проектов](../../extensibility/internals/creating-project-types.md)