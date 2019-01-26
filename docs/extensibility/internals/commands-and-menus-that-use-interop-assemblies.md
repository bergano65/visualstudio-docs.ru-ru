---
title: Команды и меню, которые используют сборки взаимодействия | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 116c7e3adf8b8d75b96d70e25fb0bd173ff9474e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984695"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Команды и меню, которые используют сборки взаимодействия
Пакет VSPackage, реализующий команды меню и панель инструментов с помощью сборок взаимодействия должен:  
  
- Сообщите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) о команды, он поддерживает и доступны ли они в настоящее время.  
  
- Следовать правилам (контракт) для обработки команды.  
  
- Явная реализация обработка команд с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейс.  
  
  Следующий раздел описывает, как выполнить эти задачи.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Определение состояния команды с помощью сборок взаимодействия](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Описывает, как VSPackage сообщает ей, о какие команды поддерживаются и доступны ли они в настоящее время.  
  
 [Контракты команд в сборках взаимодействия](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Предоставляет определение базовая команда контракта, используемого приложением всех пакетов VSPackage, реализация команд, с помощью сборок взаимодействия.
  
 [Реализация команды](../../extensibility/internals/command-implementation.md)  
 Предоставляет общие сведения о том, как VSPackage реализует команду.  
  
 [Регистрация обработчиков команд сборки взаимодействия](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Описывает записи реестра, необходимые для уведомления IDE, что VSPackage предоставляет обработчик команды.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Доступность команд](../../extensibility/internals/command-availability.md)  
 Описывает условия, используемые в интегрированной среде разработки, чтобы определить, какие команды VSPackage доступны и какие объект обрабатывает их.  
  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Сведения о том, как создать пользовательский Интерфейс, который использует [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] команды поддержки.  
  
 [Маршрутизация команд в пакеты VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Обзор процесса, используемого для связи объекта с запросом нужную команду.