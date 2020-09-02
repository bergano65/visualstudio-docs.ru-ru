---
title: Маршрутизация команд в пакетах VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 954d3f25a425652d8adcb31bd36fab06de0d04d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195091"
---
# <a name="command-routing-in-vspackages"></a>Маршрутизация команд в пакетах VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Команда направляется в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] зависимости от контекста, в котором она выполняется. Он направляется от первоначального контекста к глобальному контексту.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Алгоритм маршрутизации](../../extensibility/internals/command-routing-algorithm.md)  
 Описывает порядок разрешения маршрутизации команд.  
  
 [Доступность](../../extensibility/internals/command-availability.md)  
 Обсуждается маршрутизация команд.  
  
 [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Обсуждаются вопросы в командах маршрутизации между управляемым кодом и COM.  
  
## <a name="related-sections"></a>См. также  
 [Объекты контекста выбора](../../extensibility/internals/selection-context-objects.md)  
 Обсуждается модель того, как можно определить фокус контекста выбора пользователя в окне.  
  
 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.
