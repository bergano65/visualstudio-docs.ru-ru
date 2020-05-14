---
title: Создание типов проектов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709068"
---
# <a name="create-project-types"></a>Создание типов проектов
Вы можете [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] расширить, создав новый тип проекта. Чтобы создать новый тип проекта, необходимо понять несколько концепций и выполнить ряд шагов. Ниже приведены общие темы, в ходе как создавать типы проектов.

## <a name="in-this-section"></a>В этом разделе
- [Решения по проектированию типов проектов](../../extensibility/internals/project-type-design-decisions.md)

 Обсуждает элемент, сохранение файла проекта и решения по механике обязательств, которые необходимо принять перед созданием нового типа проекта.

- [Контрольный список: Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)

 Предоставляет обзор шагов, которые необходимо выполнить для создания нового типа проекта, который поддерживает такие задачи программирования, как редактирование кода и компиляция, создание, отладка и развертывание приложений в проекте.

- [Создание экземпляров проектов с помощью проектных фабрик](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Предоставляет информацию о том, как предоставить и использовать фабрику проектов для создания экземпляров нового проекта.

- [Регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md)

 Предоставляет образцы кода заявлений из реестра, которые предоставляют пути и данные по умолчанию, а также таблицу, содержащую записи из скрипта реестра для каждой выписки.

- [Настойчивость проекта](../../extensibility/internals/project-persistence.md)

 Обсуждается использование `IPersistFileFormat` для сохранения как файлов, так и объектов проекта, не связанных с файлами.

- [Используйте MSBuild](../../extensibility/internals/using-msbuild.md)

 Описывает, как ваш тип [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] проекта может использовать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] движок сборки, чтобы позволить пользователям строить из и на командной строке.

## <a name="related-sections"></a>См. также
- [Поддержка инструментов просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Объясняет архитектуру инструментов просмотра кода, таких как **браузер объектов** и окно **просмотра классов.** Описывает интерфейсы и методы, используемые для реализации просмотра объектов в VSPackage.

- [Добавление шаблонов элементов проекта и проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)

 Обсуждаетзначение, которое играют проекты при определении того, какой редактор используется при открытии элемента проекта и как можно манипулировать ресурсами проекта.

- [Установка VSPackages с установкой Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Показывает, как придать VSPackage свою уникальную идентичность и как обернуть ваш VSPackage DLLs и другую информацию в пакете установки Windows (*. Файл MSI)* для развертывания для ваших клиентов.

- [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Описывает, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] как представления и адреса иерархий.

- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)

 Предоставляет обзор VSPackage, установимый объект COM, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] который расширяет среду и обсуждает, как реализовать свой собственный VSPackage.

- [Типы проектов](../../extensibility/internals/project-types.md)

 Обсуждает, как использовать проекты для изменения кода, компиляции и сборки кода, а также запуска и отладки кода, а также предоставляет ссылки на подробные темы о том, как создавать типы проектов.
