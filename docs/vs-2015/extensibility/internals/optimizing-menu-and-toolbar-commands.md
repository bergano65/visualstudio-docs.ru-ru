---
title: Оптимизация меню и команды панели инструментов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25a721c77269837ad8d158db186274586ad638df
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993398"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Оптимизация команд меню и панелей инструментов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Добавление пакетов VSPackage и их соответствующие команды, чтобы [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] может привести к загромождению пользовательского интерфейса. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] предоставляет способы путаницы пользовательского интерфейса команды.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Как сделать команды доступными](../../extensibility/internals/making-commands-available.md)  
 Приводятся общие рекомендации по минимизации частенько получает сильнейший из [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пользовательского интерфейса при добавлении пакетов VSPackage.  
  
 [Рекомендации по размещению](../../extensibility/internals/command-placement-guidelines.md)  
 Предоставляет конкретные рекомендации для реализации VSPackage в соответствии с размером набора команд.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.
