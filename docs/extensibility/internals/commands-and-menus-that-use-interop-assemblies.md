---
title: Команды и меню, которые используют Interop ассамблеи (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709489"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Команды и меню, в которые используются сборки Interop
VSPackage, который реализует команды меню и панели инструментов с помощью сборок Interop, должен:

- Сообщите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) о командах, которые она поддерживает, и о том, включены ли они в настоящее время.

- Придерживайтесь правил (контракта) для обработки команд.

- Явно реализуем обработку <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> команд, используя интерфейс или интерфейс.

  В следующем разделе описывается, как выполнять эти задачи.

## <a name="in-this-section"></a>В этом разделе
- [Определить состояние команды с помощью сборок Interop](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Описывает, как VSPackage уведомляет IDE о том, какие команды он поддерживает и включены ли они в настоящее время.

- [Командные контракты в ассамблеях Interop](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Предоставляет определение базового командного контракта, используемого всеми командами VSPackages, реализующими команды с использованием сборок Interop.

- [Реализация командования](../../extensibility/internals/command-implementation.md)

 Предоставляет обзор того, как VSPackage реализует команду.

- [Регистрация обработчиков командных команд Interop](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Описывает записи реестра, необходимые для уведомления IDE о том, что VSPackage предоставляет обработчик команд.

## <a name="related-sections"></a>См. также
- [Доступность команд](../../extensibility/internals/command-availability.md)

 Описывает критерии, используемые IDE для определения того, какие команды VSPackage доступны и какой объект обрабатывает их.

- [Как VSPackages добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Предоставляет подробную информацию о том, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] как создать ui, используюстороню поддержку команд.

- [Командная размытая в VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Обзор процесса, используемого для соотнесения объекта с правильным запросом команды.
