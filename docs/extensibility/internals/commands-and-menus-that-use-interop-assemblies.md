---
title: "Команды и меню, использования сборок взаимодействия | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c0d2cf9218743ec21121d849482e5a3086b36ab2
ms.lasthandoff: 02/22/2017

---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Команды и меню, использования сборок взаимодействия
VSPackage, реализующий команды меню и панель инструментов с помощью сборок взаимодействия необходимо:  
  
-   Сообщить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) о команды, она поддерживает и доступны ли они в настоящее время.  
  
-   Следует правилам (контракт) для обработки команды.  
  
-   Явно реализовать обработку команд с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
 Ниже описывается, как выполнять эти задачи.  
  
## <a name="in-this-section"></a>Содержание  
 [Определение состояния команды с помощью сборок взаимодействия](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Описывает, как VSPackage сообщает IDE о какие команды поддерживаются и доступны ли они в настоящее время.  
  
 [Команда контрактов в сборках взаимодействия](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Предоставляет определение контракта базовой команды, используемые все пакеты VSPackage, реализация команд с помощью сборок взаимодействия  
  
 [Реализация](../../extensibility/internals/command-implementation.md)  
 Общие сведения о реализации команды VSPackage.  
  
 [Регистрация обработчиков команд сборки взаимодействия](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Описание записи реестра, необходимые для уведомления интегрированной среды разработки, что VSPackage предоставляет обработчик команды.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Доступность](../../extensibility/internals/command-availability.md)  
 Описывает условия, используемые для определения доступных команд VSPackage и какие объект обрабатывает их в интегрированной среде разработки.  
  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Предоставляет подробные сведения о том, как создать пользовательский Интерфейс, который использует [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] команды поддержки.  
  
 [Маршрутизация команд в пакеты VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 Обзор процесса, используемого для связи объекта с запросом нужную команду.
