---
title: "Команда маршрутизации в пакетах VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ffbfb131eedb316c321bbf955ec7cc2951c71b8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="command-routing-in-vspackages"></a>Маршрутизация команд в пакеты VSPackage
Команда направляется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] на основе контекста, в котором он выполняется. Он направляется из исходного контекста наружу в глобальном контексте.  
  
## <a name="in-this-section"></a>Содержание  
 [Алгоритм маршрутизации](../../extensibility/internals/command-routing-algorithm.md)  
 Описывает порядок маршрутизации выполнения команды.  
  
 [Доступность](../../extensibility/internals/command-availability.md)  
 Описывает маршрутизация команд.  
  
 [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Обсуждаются вопросы, связанные с команды маршрутизации между управляемым кодом и COM.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Объекты контекста выбора](../../extensibility/internals/selection-context-objects.md)  
 Рассматривается определение пользователя Выбор контекста фокус на окно модель.  
  
 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.