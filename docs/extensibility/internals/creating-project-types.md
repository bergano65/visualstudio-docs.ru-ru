---
title: "Создание типов проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1ab4f9f41fc2e98fcc9b2f7a9aeec6885e3b3005
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="creating-project-types"></a>Создание типов проектов
Вы можете расширить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , создав новый тип проекта. Чтобы создать новый тип проекта, необходимо понимать некоторые понятия и выполнить ряд шагов. В следующих разделах приводятся общие сведения о создании типов проектов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Проектные решения для проекта решений](../../extensibility/internals/project-type-design-decisions.md)  
 Описание элемента, сохранения файлов проекта и обязательств выразил проектные решения, которые необходимо внести, прежде чем создавать новый тип проекта.  
  
 [Контрольный список. Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Обзор шагов, которые необходимо выполнить, чтобы создать новый тип проекта, который поддерживает задачи программирования, как редактирование кода и компиляции, построения, отладки и развертывания приложений в своем проекте.  
  
 [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Сведения о том, как для предоставления и использования фабрики проектов для создания экземпляров нового проекта.  
  
 [Регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md)  
 Предоставляет образцы кода, инструкций из реестра, предоставляющие пути по умолчанию и данных и таблицы, содержащие записи из реестра скрипта для каждой инструкции.  
  
 [Сохранение проекта](../../extensibility/internals/project-persistence.md)  
 Описывает использование `IPersistFileFormat` для сохранения файла и объекты не под управлением файла проекта.  
  
 [Использование MSBuild](../../extensibility/internals/using-msbuild.md)  
 Описывает способ использования типа проекта [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] обработчика, чтобы позволить пользователям строится на основе построения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и из командной строки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Описывается архитектура кода, такие как средства просмотра **обозревателя объектов** и **представление классов** окна. Описывает интерфейсы и методы, используемые для реализации обозревателя объектов в VSPackage.  
  
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Описывается важность, проекты воспроизведение при определении того, какой редактор используется при открытии элемента проекта и как можно управлять ресурсами проекта.  
  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Показывает, как предоставить свой собственный уникальный идентификатор пакета VSPackage и заключать VSPackage библиотеки DLL и другие сведения в пакет установщика Windows (. MSI-файл) для развертывания клиентов.  
  
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Описывает способ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] иерархии, представления и адреса.  
  
 [Пакеты VSPackage](../../extensibility/internals/vspackages.md)  
 Общие сведения о VSPackage, устанавливаемые COM-объект, который расширяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды и описывается, как реализовать собственные VSPackage.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Описывается использование проектов для изменения кода, компиляция и сборка кода и выполнять и отлаживать код и ссылки на подробные статьи о создании типов проектов.