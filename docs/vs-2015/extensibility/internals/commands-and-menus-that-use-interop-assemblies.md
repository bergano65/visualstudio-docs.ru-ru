---
title: Команды и меню, которые используют сборки взаимодействия | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad6b324953914df7103d0dec7371199e3cbbd937
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989598"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Команды и меню, которые используют сборки взаимодействия
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакет VSPackage, реализующий команды меню и панель инструментов с помощью сборок взаимодействия должен:  
  
- Сообщите [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среды разработки (IDE) о команды, он поддерживает и доступны ли они в настоящее время.  
  
- Следовать правилам (контракт) для обработки команды.  
  
- Явная реализация обработка команд с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейс.  
  
  Ниже описано, как выполнить эти задачи.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Определение состояния команды с помощью сборок взаимодействия](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Описывает, как VSPackage сообщает ей, о какие команды поддерживаются и доступны ли они в настоящее время.  
  
 [Контракты команд в сборках взаимодействия](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Предоставляет определение базовая команда контракта, используемого приложением всех пакетов VSPackage, реализация команд, с помощью сборок взаимодействия  
  
 [Реализация](../../extensibility/internals/command-implementation.md)  
 Предоставляет общие сведения о том, как VSPackage реализует команду.  
  
 [Регистрация обработчиков команд сборки взаимодействия](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Описывает записи реестра, необходимые для уведомления IDE, что VSPackage предоставляет обработчик команды.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Доступность](../../extensibility/internals/command-availability.md)  
 Описывает условия, используемые в интегрированной среде разработки, чтобы определить, какие команды VSPackage доступны и какие объект обрабатывает их.  
  
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Сведения о том, как создать пользовательский Интерфейс, который использует [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] команды поддержки.  
  
 [Маршрутизация команд в пакетах VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Обзор процесса, используемого для связи объекта с запросом нужную команду.
