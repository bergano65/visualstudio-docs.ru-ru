---
title: Создание типов проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c3d983da91fadbb0eb78eab6d0fa5bb02cca193
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606021"
---
# <a name="create-project-types"></a>Создание типов проектов
Вы можете расширить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , создав новый тип проекта. Чтобы создать новый тип проекта, необходимо понимать несколько базовых понятий и выполнить ряд действий. В следующих разделах приводятся общие сведения для создания типов проектов.

## <a name="in-this-section"></a>Содержание раздела
- [Проектные решения проекта](../../extensibility/internals/project-type-design-decisions.md)

 Описание элемента, сохранение файла проекта и обязательства механику проектные решения, которые необходимо принять, прежде чем создавать новый тип проекта.

- [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)

 Обзор шагов, которые необходимо выполнить, чтобы создать новый тип проекта, который поддерживает такие задачи программирования, как редактирование кода и компиляция, построения, отладки и развертывания приложений в вашем проекте.

- [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Сведения о том, как предоставить и использовать фабрику проекта для создания экземпляров нового проекта.

- [Регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md)

 Примеры кода, инструкций из реестра, которые предоставляют путей по умолчанию и данных и таблицы, содержащие записи из скрипта реестра для каждой инструкции.

- [Сохранение проекта](../../extensibility/internals/project-persistence.md)

 Обсуждается использование `IPersistFileFormat` для сохранения файла и объектов-нефайловых проекта.

- [Использование MSBuild](../../extensibility/internals/using-msbuild.md)

 Описывается, как можно использовать тип проекта [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] обработчика, чтобы позволить пользователям строится на основе построения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и в командной строке.

## <a name="related-sections"></a>Связанные разделы
- [Поддержка средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Описывается архитектура кода, такие как средства просмотра **обозреватель объектов** и **представление классов** окна. Описывает интерфейсы и методы, используемые для реализации просмотра объектов в VSPackage.

- [Добавьте в проект и шаблоны элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Обсуждается важность, проекты воспроизвести при определении того, какой редактор используется при открытии элемента проекта и как можно управлять ресурсами проекта.

- [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Показано, как предоставить свой собственный уникальный идентификатор пакета VSPackage и как программы-оболочки для библиотеки DLL VSPackage и другие сведения в пакет установщика Windows (*. MSI* файл) для развертывания клиентов.

- [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Описывает способ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] иерархий представлений и адреса.

- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)

 Общие сведения о VSPackage, устанавливаемый объект COM, который расширяет [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды и обсуждается реализация собственных VSPackage.

- [Типы проектов](../../extensibility/internals/project-types.md)

 Описывает, как использовать проекты для изменения кода, компиляции и сборки кода и выполнять и отлаживать код и ссылки на подробные разделы о создании типов проектов.