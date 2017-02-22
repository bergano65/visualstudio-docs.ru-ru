---
title: "Оптимизация меню и команды панели инструментов | Microsoft Docs"
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
  - "команды [Visual Studio], меню"
  - "команды [Visual Studio], панелей инструментов"
  - "меню [Visual Studio SDK] команды"
  - "команды меню, реализация"
  - "панели инструментов [Visual Studio], команды"
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Оптимизация меню и команды панели инструментов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Добавление пакетов VSPackages и их соответствующих команд в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] может вызвать много пользовательского интерфейса.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет способы для сведения к минимуму путаницы команд пользовательского интерфейса.  
  
## В этом подразделе  
 [Доступность команд](../../extensibility/internals/making-commands-available.md)  
 Приводятся общие рекомендации по минимизации правило из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса при добавлении пакетов VSPackages.  
  
 [Рекомендации по размещению](../../extensibility/internals/command-placement-guidelines.md)  
 Предоставляет конкретные рекомендации для реализации в соответствии с размером набора команд в VSPackage.  
  
## Связанные подразделы  
 [Команды, меню и панелей инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский Интерфейс, который включает меню, панелей инструментов и команд со списком.