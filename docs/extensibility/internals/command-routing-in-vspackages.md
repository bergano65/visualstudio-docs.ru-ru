---
title: Команда маршрутизации в пакетах VSPackage | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 58be191a3b7a2256d0883e313f77b264f6be4d69
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135807"
---
# <a name="command-routing-in-vspackages"></a>Маршрутизация команд в пакеты VSPackage
Команда направляется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] на основе контекста, в котором он выполняется. Он направляется из исходного контекста наружу в глобальном контексте.  
  
## <a name="in-this-section"></a>В этом разделе  
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