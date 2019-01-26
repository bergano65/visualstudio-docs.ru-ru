---
title: Оптимизация меню и команды панели инструментов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c68822c2dc640008079b0d518fb5774be9a46ea6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037750"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Оптимизация команд меню и панелей инструментов
Добавление пакетов VSPackage и их соответствующие команды, чтобы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] может привести к загромождению пользовательского интерфейса. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет способы путаницы пользовательского интерфейса команды.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Как сделать команды доступными](../../extensibility/internals/making-commands-available.md)  
 Приводятся общие рекомендации по минимизации частенько получает сильнейший из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса при добавлении пакетов VSPackage.  
  
 [Рекомендации по размещению](../../extensibility/internals/command-placement-guidelines.md)  
 Предоставляет конкретные рекомендации для реализации VSPackage в соответствии с размером набора команд.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.