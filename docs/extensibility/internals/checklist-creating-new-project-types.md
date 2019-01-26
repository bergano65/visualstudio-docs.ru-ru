---
title: 'Контрольный список: Создание типов проектов | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e0c5f170e64833a20774d21bed04c9d4728dc06
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951954"
---
# <a name="checklist-create-new-project-types"></a>Контрольный список: Создание новых типов проектов
Необходимо выполнить несколько задач, чтобы создать новый тип проекта. Следующий контрольный список содержит указания для этих задач:  
  
1.  Проектируйте функциональность для нового типа проекта. Дополнительные сведения см. в разделе [проектные решения проекта](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Определите, какие редакторы используются для кода и других элементов проекта. Вы можете использовать основные или стандартные редакторы, или можно создать и использовать проекту относящимся редакторам. Дополнительные сведения см. в разделе [создание специализированных редакторов и конструкторов](../../extensibility/creating-custom-editors-and-designers.md) и [как: Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Определить уровень своего участия, будет иметь элементы проекта в **представление классов** и **обозреватель объектов**. Дополнительные сведения см. в разделе [поддерживает средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Произвести новые классы, в зависимости от проектные решения, сделанным ранее для проекта и элементов проекта.  
  
5.  Написание кода для следующих компонентов типа проекта:  
  
    -   Фабрика проекта для управления, создание новых проектов и Открытие существующих проектов. Дополнительные сведения см. в разделе [создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Проект иерархии и обработка команд. Дополнительные сведения см. в разделе [HierUtil7 используйте классы проекта в реализации типа проекта (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md), [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)и [ Команды MenuCommand и OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Элементы управления проектами, включая добавление проекта к **новый проект** диалоговое окно. Дополнительные сведения см. в разделе [добавить проект и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Длительное хранение состояния проекта и отдельных элементов. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md). Для сохранения информации о решении, см. в разделе [решения](../../extensibility/internals/solutions.md).  
  
    -   Свойства конфигурациями для отображения в окне «Свойства». Дополнительные сведения см. в разделе [расширять свойства](../../extensibility/internals/extending-properties.md).  
  
    -   Свойствам конфигурации проекта, реализованное на страницах свойств для отображения свойства, зависимые от конфигурации. Дополнительные сведения см. в разделе [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Перечисление выходных данных для развертывания. Дополнительные сведения см. в разделе [конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Служб запуска проекта. Дополнительные сведения см. в разделе [элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md) и [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md).  
  
    -   Объекты и классы, производные от `IDispatch`, которые доступны для автоматизации.  
  
    -   Таблицы команд XML (*.vsct*) файлы. Дополнительные сведения см. в разделе [Visual Studio командные table (.vsct) файлы](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Проверки, отладки и запуска типа проекта.  
  
7.  Отображения проекта в **проекта** вкладке **добавить ссылку** диалоговое окно, задав `VARIANT_TRUE` как значение для `VSHPROPID_ShowProjInSolutionPage`. Дополнительные сведения см. в разделах <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Создание установщика Microsoft (*.msi*) файла для установки пакетов VSPackage. Дополнительные сведения см. в разделе [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [регистрации типа проекта](../../extensibility/internals/registering-a-project-type.md), и [пакетов VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>См. также  
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)   
 [Создание типов проектов](../../extensibility/internals/creating-project-types.md)