---
title: 'Контрольный список: Создание новых типов проектов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 11707e62e99dd6a7920ad627d02e6e418c002e80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131993"
---
# <a name="checklist-creating-new-project-types"></a>Контрольный список: Создание новых типов проектов
Необходимо выполнить несколько задач, чтобы создать новый тип проекта. Следующий контрольный список содержится руководство для этих задач.  
  
1.  Проектирование функциональные возможности для нового типа проекта. Дополнительные сведения см. в разделе [проектные решения проекта типа](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Определите, какие редакторы используются для кода и других элементов проекта. Можно использовать основной или стандартные редакторы, или можно создать и использовать редакторы для конкретного проекта. Дополнительные сведения см. в разделе [создания пользовательских редакторов и конструкторов](../../extensibility/creating-custom-editors-and-designers.md) и [как: открытие редакторов конкретного проекта](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Определить уровень своего участия, будет иметь элементы проекта в **представление классов** и **обозревателя объектов**. Дополнительные сведения см. в разделе [средства обзора поддержка символов](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Произвести новые классы, основанные на проектных решениях, сделанные ранее для проектов и элементов проектов.  
  
5.  Написание кода для следующих компонентов типа проектов:  
  
    -   Фабрика проекта для управления создание новых проектов и открытия существующих проектов. Дополнительные сведения см. в разделе [Создание проекта экземпляров, с помощью проекта фабрик](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Иерархия проекта и обработке команд. Дополнительные сведения см. в разделе [не в сборке: с помощью HierUtil7 проекта классов для реализации типа проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md), [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)и [команды MenuCommand и. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Элементы управления проектами, включая добавление проекта, чтобы **новый проект** диалоговое окно. Дополнительные сведения см. в разделе [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md) и [регистрация проекта и шаблонов элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Сохраняемость состояния проекта и отдельных элементов. Дополнительные сведения см. в разделе [открытия и сохранения элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md). Сохранение информации о решении, в разделе [решения](../../extensibility/internals/solutions.md).  
  
    -   Независимые свойства конфигурации для отображения в окне «Свойства». Дополнительные сведения см. в разделе [расширение свойств](../../extensibility/internals/extending-properties.md).  
  
    -   Свойства конфигурации проекта, как осуществляется на странице свойств отображаются свойства, зависящие от конфигурации. Дополнительные сведения см. в разделе [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Перечисление выходных данных для развертывания. Дополнительные сведения см. в разделе [конфигурации проекта для вывода](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Проект при запуске службы. Дополнительные сведения см. в разделе [элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md) и [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md).  
  
    -   Объекты и классы, производные от `IDispatch`, доступные для автоматизации.  
  
    -   Файлы таблицы команд XML (.vsct). Дополнительные сведения см. в разделе [Visual Studio Command Table (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Тестирования, отладки и запуска типа проекта.  
  
7.  Отобразить проект в **проекта** вкладке **добавить ссылку** диалоговое окно, задав `VARIANT_TRUE` значение `VSHPROPID_ShowProjInSolutionPage`. Дополнительные сведения см. в разделах <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Создайте файл установщика Microsoft (MSI) для установки пакетов VSPackage. Дополнительные сведения см. в разделе [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [регистрации типа проекта](../../extensibility/internals/registering-a-project-type.md), и [пакетов VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>См. также  
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)   
 [Создание типов проектов](../../extensibility/internals/creating-project-types.md)