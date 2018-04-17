---
title: Команды и меню, которые использовать сборки взаимодействия | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c48ee7eb25fa95789076454c849485f4ac1dc384
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Команды и меню, которые использовать сборки взаимодействия
Пакет VSPackage, реализующий команды меню и панель инструментов с помощью сборок взаимодействия должен:  
  
-   Сообщить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) о командах, он поддерживает, а также доступны ли они в настоящее время.  
  
-   Соответствуют правилам (контракт) для обработки команды.  
  
-   Явная реализация обработку команд с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейса.  
  
 Далее описывается, как выполнять эти задачи.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Определение состояния команды с помощью сборок взаимодействия](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Описывает, как VSPackage сообщает IDE о какие команды поддерживаются и доступны ли они в настоящее время.  
  
 [Контракты команд в сборках взаимодействия](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Предоставляет определение контракта основные команды, используемые все пакеты VSPackage, реализующий команд с помощью сборок взаимодействия  
  
 [Реализация](../../extensibility/internals/command-implementation.md)  
 Предоставляет общие сведения о том, как VSPackage реализует команду.  
  
 [Регистрация обработчиков команд сборки взаимодействия](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Описание записи реестра, необходимые для уведомления IDE, что VSPackage предоставляет обработчик команд.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Доступность](../../extensibility/internals/command-availability.md)  
 Описание критериев, используемых в интегрированной среде разработки, чтобы определить список доступных команд VSPackage и какой объект обрабатывает их.  
  
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Предоставляет подробные сведения о том, как создать пользовательский Интерфейс, который использует [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] команды поддержки.  
  
 [Маршрутизация команд в пакетах VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Обзор процесса, используемых для связывания объекта с корректную команду запроса.