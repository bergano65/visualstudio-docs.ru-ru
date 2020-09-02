---
title: 'Контрольный список: создание новых типов проектов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02edc5925109a31eebfd98c90bd116fb86eef276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697226"
---
# <a name="checklist-creating-new-project-types"></a>Контрольный список. Создание новых типов проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Для создания нового типа проекта необходимо выполнить несколько задач. В следующем контрольном списке приведены инструкции по этим задачам.  
  
1. Разработайте функциональные возможности нового типа проекта. Дополнительные сведения см. в разделе [решения по проектированию типов проектов](../../extensibility/internals/project-type-design-decisions.md).  
  
2. Определите, какие редакторы используются для кода и других элементов проекта. Можно использовать редакторы Core или Standard или создавать и использовать редакторы для конкретных проектов. Дополнительные сведения см. в статьях [Создание пользовательских редакторов и конструкторов](../../extensibility/creating-custom-editors-and-designers.md) и [инструкции: открытие редакторов для конкретных проектов](../../extensibility/how-to-open-project-specific-editors.md).  
  
3. Определите уровень участия, которые будут иметь элементы проекта в **представление классов** и **обозревателе объектов**. Дополнительные сведения см. в разделе [Поддержка средств просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4. Создавайте новые классы на основе решений, принятых ранее для проекта и элементов проекта.  
  
5. Напишите код для следующих компонентов типа проекта:  
  
    - Фабрика проектов для управления созданием новых проектов и открытия существующих проектов. Дополнительные сведения см. в разделе [Создание экземпляров проекта с помощью фабрик проекта](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    - Иерархия проектов и обработка команд. Дополнительные сведения см. в разделе [не в сборке. Использование классов проектов HierUtil7 для реализации типа проекта (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346), [элементов модели проекта](../../extensibility/internals/elements-of-a-project-model.md), [основных компонентов модели проекта](../../extensibility/internals/project-model-core-components.md) и команды MenuCommand и [олеменукоммандс](../../misc/menucommands-vs-olemenucommands.md).  
  
    - Управление элементами проекта, включая добавление проекта в диалоговое окно **Новый проект** . Дополнительные сведения см. в разделе [Добавление шаблонов проектов и элементов проектов](../../extensibility/internals/adding-project-and-project-item-templates.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    - Сохраняемость состояния проекта и отдельных элементов. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md). Сведения о сохранении сведений о решении см. в разделе [решения](../../extensibility/internals/solutions-overview.md).  
  
    - Независимые от конфигурации свойства, отображаемые в окно свойств. Дополнительные сведения см. в разделе [расширение свойств](../../extensibility/internals/extending-properties.md).  
  
    - Свойства конфигурации проекта, реализованные на страницах свойств, для отображения свойств, зависящих от конфигурации. Дополнительные сведения см. в разделе [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
    - Перечисление выходных данных для развертывания. Дополнительные сведения см. в разделе [Конфигурация проекта для выходных данных](../../extensibility/internals/project-configuration-for-output.md).  
  
    - Службы запуска проектов. Дополнительные сведения см. в разделе [элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md) и [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md).  
  
    - Объекты, или классы, производные от `IDispatch` , доступны для автоматизации.  
  
    - Файлы таблицы команд XML (. vsct). Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6. Тестирование, отладка и запуск типа проекта.  
  
7. Откройте проект на вкладке **проект** диалогового окна **Добавление ссылки** , задав в `VARIANT_TRUE` качестве значения параметра `VSHPROPID_ShowProjInSolutionPage` . Дополнительные сведения см. в разделах <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8. Создайте файл установщика Microsoft (MSI) для установки пакетов VSPackage. Дополнительные сведения см. в разделе [Установка пакетов VSPackage с установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md)и [пакетов VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>См. также:  
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)   
 [Создание типов проектов](../../extensibility/internals/creating-project-types.md)
