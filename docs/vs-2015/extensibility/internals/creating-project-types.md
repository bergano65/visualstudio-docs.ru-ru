---
title: Создание типов проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994299"
---
# <a name="creating-project-types"></a>Создание типов проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вы можете расширить [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , создав новый тип проекта. Чтобы создать новый тип проекта, необходимо понимать несколько базовых понятий и выполнить ряд действий. В следующих разделах приводятся общие сведения для создания типов проектов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Проектные решения для проекта решений](../../extensibility/internals/project-type-design-decisions.md)  
 Описание элемента, сохранение файла проекта и обязательства механику проектные решения, которые необходимо принять, прежде чем создавать новый тип проекта.  
  
 [Контрольный список: Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Обзор шагов, которые необходимо выполнить, чтобы создать новый тип проекта, который поддерживает задачи программирования, как редактирование кода и компиляция, построения, отладки и развертывания приложений в вашем проекте.  
  
 [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Сведения о том, как предоставить и использовать фабрику проекта для создания экземпляров нового проекта.  
  
 [Регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md)  
 Примеры кода, инструкций из реестра, которые предоставляют путей по умолчанию и данных и таблицы, содержащие записи из скрипта реестра для каждой инструкции.  
  
 [Сохранение проекта](../../extensibility/internals/project-persistence.md)  
 Обсуждается использование `IPersistFileFormat` для сохранения файла и объектов-нефайловых проекта.  
  
 [Использование MSBuild](../../extensibility/internals/using-msbuild.md)  
 Описывается, как можно использовать тип проекта [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] обработчика, чтобы позволить пользователям строится на основе построения [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и в командной строке.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Описывается архитектура кода, такие как средства просмотра **обозреватель объектов** и **представление классов** окна. Описывает интерфейсы и методы, используемые для реализации просмотра объектов в VSPackage.  
  
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Обсуждается важность, проекты воспроизвести при определении того, какой редактор используется при открытии элемента проекта и как можно управлять ресурсами проекта.  
  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Показано, как предоставить свой собственный уникальный идентификатор пакета VSPackage и как программы-оболочки для библиотеки DLL VSPackage и другие сведения в пакет установщика Windows (. MSI-файл) для развертывания клиентов.  
  
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Описывает способ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] иерархий представлений и адреса.  
  
 [Пакеты VSPackage](../../extensibility/internals/vspackages.md)  
 Общие сведения о VSPackage, устанавливаемый объект COM, который расширяет [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среды и обсуждается реализация собственных VSPackage.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Описывает, как использовать проекты для изменения кода, компиляции и сборки кода и выполнять и отлаживать код и ссылки на подробные разделы о создании типов проектов.
