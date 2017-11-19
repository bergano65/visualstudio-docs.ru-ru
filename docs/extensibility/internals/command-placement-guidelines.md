---
title: "Команда рекомендации по размещению | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e74bda24459bedeef007b451c7fabe3922e7ab37
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="command-placement-guidelines"></a>Рекомендации по размещению команды
Советы и рекомендации для позиционирования команд в среде разработки Visual Studio (IDE) зависит от размера набора команд. Команды определяются и располагается в соответствии с данными в vsct-файлами.  
  
## <a name="best-practices-for-all-command-sets"></a>Советы и рекомендации для всех наборов команд  
 Для каждого набора команд придерживайтесь следующих правил.  
  
-   Подготовка плана структура команды заранее. Определите команды, поля со списком, группы команд и контекстные меню, которые будут использоваться в нескольких местах.  
  
-   Команды, которые отображаются в одной группе должен быть связан.  
  
-   Группы, содержащие только одной команды являются допустимыми.  
  
-   Пакеты не следует добавлять большое количество команд существующими меню Visual Studio. Вместо этого они должны создать меню или подменю для размещения новых команд.  
  
-   Если поместить команду существующее меню, имя команды, чтобы его назначение было понятно и не следует путать с существующие команды.  
  
## <a name="best-practices-for-small-command-sets"></a>Советы и рекомендации по наборы небольших команд  
 Если вы разрабатываете пакет VSPackage, который имеет несколько команд, также необходимо выполните следующее:  
  
-   По возможности используйте [родительского элемента](../../extensibility/parent-element.md) команды, поле со списком, группы или дочернего меню, чтобы поместить его в соответствующую группу.  
  
-   Назначьте эти группы меню, отображаемых в пакете VSPackage.  
  
-   Должен быть родительским для дочернего меню или команды [элемент группы](../../extensibility/group-element.md). Команды и дочерних меню назначаются группам, а затем присвоить группы родительского меню.  
  
-   Команду можно поместить в дополнительные группы, добавив [элемент CommandPlacements](../../extensibility/commandplacements-element.md) статьи после определения команды, а затем добавление к `CommandPlacements Element` [CommandPlacement элемент](../../extensibility/commandplacement-element.md) для каждого Дополнительные группы.  
  
## <a name="best-practices-for-large-command-sets"></a>Советы и рекомендации для команды больших наборов данных  
 Если для вашего VSPackage многие команды, которые будут отображаться в нескольких контекстах, также необходимо выполните следующее:  
  
-   Убедитесь в меню, группы и команды самостоятельно родительские связи. То есть, не будут назначены `Parent Element` в определении элемента.  
  
-   Используйте `CommandPlacement Element` записей в `CommandPlacements Element` раздел, чтобы поместить в их родительского меню и группы меню, групп и команд.  
  
-   В `CommandPlacements` статьи, операции, которые заполнения данного меню или группа должны иметь рядом друг с другом. Это помогает читаемость и делает `Priority` проще определить ранжирование.  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)