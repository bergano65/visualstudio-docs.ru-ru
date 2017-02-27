---
title: "Контрольный список: Создание новых типов проектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Создание новых типов проектов [Visual Studio SDK]"
  - "Контрольный список для создания типов проектов"
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Контрольный список: Создание новых типов проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Необходимо выполнить ряд задач, чтобы создать новый тип проекта. В следующем контрольном руководство для этих задач.  
  
1.  Проектирование функциональности для нового типа проекта. Дополнительные сведения см. в разделе [Тип проекта решений](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Определите, какие редакторы используются для кода и других элементов проекта. Можно использовать основные или стандартные редакторы, или можно создать и использовать редакторы конкретного проекта. Дополнительные сведения см. в разделах [Создание пользовательские редакторы и конструкторы](../../extensibility/creating-custom-editors-and-designers.md) и [Практическое руководство: открытие редакторов конкретного проекта](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Определите уровень своего участия, будет иметь элементы проекта в **Представление классов** и **обозревателя объектов**. Дополнительные сведения см. в разделе [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Произвести новые классы, в зависимости от решения, сделанные ранее для проектов и элементов проектов.  
  
5.  Напишите код для следующих компонентов типа проекта.  
  
    -   Фабрика проекта для управления создания новых проектов и открытия существующих проектов. Дополнительные сведения см. в разделе [Создание экземпляров проекта с помощью фабрик проекта](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Иерархия проекта и обработка команд. Дополнительные сведения см. в разделе [не в построении: с помощью HierUtil7 проект классы для реализации типа проекта \(C\+\+\)](http://msdn.microsoft.com/ru-ru/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md), [Основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md) и [команды MenuCommand и OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Элементы управления проектами, включая добавление проекта, чтобы **Новый проект** диалоговое окно. Дополнительные сведения см. в разделах [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md) и [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Сохранение состояния проекта и отдельных элементов. Для получения дополнительной информации см. [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md). Для сохранения информации о решении, в разделе [Решения](../../extensibility/internals/solutions.md).  
  
    -   Независимые свойства конфигурации для отображения в окне «Свойства». Для получения дополнительной информации см. [Расширение свойств](../../extensibility/internals/extending-properties.md).  
  
    -   Свойства конфигурации проекта, реализованное на страницах свойств для отображения свойства, зависящие от конфигурации. Дополнительные сведения см. в разделе [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Перечисление выходных данных для развертывания. Для получения дополнительной информации см. [Настройка проекта для вывода](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Службы запуска проекта. Дополнительные сведения см. в разделах [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md) и [Основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md).  
  
    -   Объекты и классы, производные от `IDispatch`, доступные для автоматизации.  
  
    -   Файлы команд XML\-таблицы \(.vsct\). Дополнительные сведения см. в разделе [Таблицы команд Visual Studio \(. Файлы Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Тестирование, отладка и запустить проект типа.  
  
7.  Отображения проекта в **проекта** вкладке **Добавить ссылку** диалоговое окно, задав `VARIANT_TRUE` значение `VSHPROPID_ShowProjInSolutionPage`. Дополнительные сведения см. в разделах <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Создание файла установщика Microsoft \(MSI\) для установки на пакеты VSPackage. Дополнительные сведения см. в разделах [Установка пакетов VSPackages с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md) и [Пакеты VSPackage](../../extensibility/internals/vspackages.md).  
  
## См. также  
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)   
 [Создание типов проектов](../../extensibility/internals/creating-project-types.md)