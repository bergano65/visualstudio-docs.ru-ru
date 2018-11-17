---
title: 'Контрольный список: Создание типов проектов | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90b48f5969a422ab9d211bb56900cf1b3b41a78b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737359"
---
# <a name="checklist-creating-new-project-types"></a>Контрольный список. Создание типов проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Необходимо выполнить несколько задач, чтобы создать новый тип проекта. Следующий контрольный список содержит указания для этих задач.  
  
1.  Проектируйте функциональность для нового типа проекта. Дополнительные сведения см. в разделе [проектные решения проекта](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Определите, какие редакторы используются для кода и других элементов проекта. Вы можете использовать основные или стандартные редакторы, или можно создать и использовать проекту относящимся редакторам. Дополнительные сведения см. в разделе [создания пользовательских редакторов и конструкторов](../../extensibility/creating-custom-editors-and-designers.md) и [как: открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Определить уровень своего участия, будет иметь элементы проекта в **представление классов** и **обозреватель объектов**. Дополнительные сведения см. в разделе [средства просмотра символов, которые поддерживают](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Произвести новые классы, в зависимости от проектные решения, сделанным ранее для проекта и элементов проекта.  
  
5.  Написание кода для следующих компонентов типа проекта:  
  
    -   Фабрика проекта для управления, создание новых проектов и Открытие существующих проектов. Дополнительные сведения см. в разделе [создание экземпляров с помощью проекта фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Проект иерархии и обработка команд. Дополнительные сведения см. в разделе [не в сборке: использование HierUtil7 проект классов для реализации типа проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md), [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)и [команды MenuCommand и. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Элементы управления проектами, включая добавление проекта к **новый проект** диалоговое окно. Дополнительные сведения см. в разделе [добавление проектов и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md) и [регистрации проекта и шаблонов элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Длительное хранение состояния проекта и отдельных элементов. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md). Для сохранения информации о решении, см. в разделе [решения](../../extensibility/internals/solutions.md).  
  
    -   Независимые свойства конфигурации для отображения в окне «Свойства». Дополнительные сведения см. в разделе [расширение свойства](../../extensibility/internals/extending-properties.md).  
  
    -   Свойствам конфигурации проекта, реализованное на страницах свойств для отображения свойства, зависимые от конфигурации. Дополнительные сведения см. в разделе [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Перечисление выходных данных для развертывания. Дополнительные сведения см. в разделе [конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Служб запуска проекта. Дополнительные сведения см. в разделе [элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md) и [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md).  
  
    -   Объекты и классы, производные от `IDispatch`, которые доступны для автоматизации.  
  
    -   Файлы таблицы команд XML (vsct-). Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Проверки, отладки и запуска типа проекта.  
  
7.  Отображения проекта в **проекта** вкладке **добавить ссылку** диалоговое окно, задав `VARIANT_TRUE` как значение для `VSHPROPID_ShowProjInSolutionPage`. Дополнительные сведения см. в разделах <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Создайте файл установщика Microsoft (MSI) для установки пакетов VSPackage. Дополнительные сведения см. в разделе [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md), и [пакетов VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>См. также  
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)   
 [Создание типов проектов](../../extensibility/internals/creating-project-types.md)

