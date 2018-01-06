---
title: "Оптимизация команды панели инструментов и меню | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f95675f420284b9d67a6d36ac30b3e71f085e565
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Оптимизация меню и команд в панели инструментов
Добавление пакетов VSPackage и их соответствующими командами в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] может вызвать центр пользовательского интерфейса. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]предоставляет способы для сведения к минимуму путаницы команды пользовательского интерфейса.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Как сделать команды доступными](../../extensibility/internals/making-commands-available.md)  
 Приводятся общие рекомендации для минимизации правило из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса при добавлении пакетов VSPackage.  
  
 [Рекомендации по размещению](../../extensibility/internals/command-placement-guidelines.md)  
 Предоставляет определенные правила для реализации VSPackage в соответствии с размером набора команд.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.