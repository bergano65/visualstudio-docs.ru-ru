---
title: "Маршрутизация команд в пакеты VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Маршрутизация команд"
  - "маршрутизация, команд Visual Studio SDK"
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Маршрутизация команд в пакеты VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Команда направляется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] на основе контекста, в котором он выполняется. Оно будет направлено от исходного контекста знаков в глобальном контексте.  
  
## В этом подразделе  
 [Алгоритм маршрутизации](../../extensibility/internals/command-routing-algorithm.md)  
 Описание порядка разрешения маршрутизации команд.  
  
 [Доступность](../../extensibility/internals/command-availability.md)  
 Описание маршрутизации команд.  
  
 [Команды и меню, использования сборок взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Рассматриваются особенности команды маршрутизации между управляемым кодом и COM.  
  
## Связанные подразделы  
 [Выбор контекста объектов](../../extensibility/internals/selection-context-objects.md)  
 Рассматривается модель, как определить пользователя Выбор контекста фокуса на окно.  
  
 [Команды, меню и панелей инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский Интерфейс, который включает меню, панелей инструментов и команд со списком.