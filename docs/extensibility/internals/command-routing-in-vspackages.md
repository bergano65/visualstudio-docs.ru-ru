---
title: Команда маршрутизации в пакетах VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 048ce0d88a87f42f5b98104d6ec928f5af8b40e2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023071"
---
# <a name="command-routing-in-vspackages"></a>Маршрутизация команд в пакеты VSPackage
Команда направляется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] на основе контекста, в котором он выполняется. Он направляется из исходного контекста наружу в глобальном контексте.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Алгоритм маршрутизации команд](../../extensibility/internals/command-routing-algorithm.md)  
 Описывает порядок маршрутизации выполнения команды.  
  
 [Доступность команд](../../extensibility/internals/command-availability.md)  
 Описание маршрутизации команд.  
  
 [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Рассматриваются особенности маршрутизированию команд между управляемым кодом и COM.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Объекты контекста выбора](../../extensibility/internals/selection-context-objects.md)  
 Обсуждается модель для как можно определить пользователя Выбор контекста фокус на окно.  
  
 [Команды, меню и панелей инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.