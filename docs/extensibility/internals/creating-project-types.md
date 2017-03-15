---
title: "Создание типов проектов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "новые типы проектов"
  - "проекты [Visual Studio SDK] новые типы проектов"
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Создание типов проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Вы можете расширить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] путем создания нового типа проекта. Чтобы создать новый тип проекта, необходимо понимать несколько базовых понятий и выполнить ряд действий. В следующих разделах приводятся общие сведения для создания типов проектов.  
  
## В этом подразделе  
 [Тип проекта решений](../../extensibility/internals/project-type-design-decisions.md)  
 Описание элемента, сохранения файлов проекта и обязательства выразил решения, необходимо сделать перед созданием нового типа проекта.  
  
 [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Обзор шагов, которые необходимо выполнить, чтобы создать новый тип проекта, который поддерживает задачи программирования, как редактирование кода и компиляции, построения, отладки и развертывания приложений в проекте.  
  
 [Создание экземпляров проекта с помощью фабрик проекта](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Сведения о том, как для предоставления и использования проекта фабрики для создания экземпляров нового проекта.  
  
 [Регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md)  
 Содержит примеры кода инструкций из реестра, предоставляющие пути по умолчанию и данных и таблицы, содержащие записи из реестра скрипта для каждой инструкции.  
  
 [Сохранение проекта](../../extensibility/internals/project-persistence.md)  
 Обсуждается использование `IPersistFileFormat` для сохранения файлов и проектов, отличных от файловых объектов.  
  
 [С помощью MSBuild](../../extensibility/internals/using-msbuild.md)  
 Описывает способ использования типа проекта [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] обработчика, чтобы позволить пользователям создавать из построения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и из командной строки.  
  
## Связанные подразделы  
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Описание архитектуры кода, такие как средства просмотра **обозревателя объектов** и **Представление классов** окна. Описывает интерфейсы и методы, используемые для реализации просмотра объектов в VSPackage.  
  
 [Добавление проекта и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Обсуждается важность, проекты для воспроизведения в определении того, какой редактор используется при открытии элемента проекта и как можно управлять ресурсами проекта.  
  
 [Установка пакетов VSPackages с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Демонстрация предоставить свой собственный уникальный идентификатор VSPackage и перенос VSPackage библиотеки DLL и другие сведения в пакет установщика Windows \(. MSI\-файл\) для развертывания клиентов.  
  
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Описывает способ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] иерархии представления и адреса.  
  
 [Пакеты VSPackage](../../extensibility/internals/vspackages.md)  
 Общие сведения о VSPackage, устанавливаемые COM\-объект, который расширяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды и обсуждается реализация собственных VSPackage.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Описывает, как использовать проекты для изменения кода, компиляции и построения кода и выполнять и отлаживать код и ссылки на разделы с подробными сведениями о том, как создавать типы проектов.