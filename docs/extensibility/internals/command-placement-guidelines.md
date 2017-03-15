---
title: "Рекомендации по размещению команды | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ca84800a199e9db420379697051fece598eb9295
ms.lasthandoff: 02/22/2017

---
# <a name="command-placement-guidelines"></a>Рекомендации по размещению команды
Советы и рекомендации для позиционирования команд в среде разработки Visual Studio (IDE) зависит от размера набора команд. Команды определяются и располагается в соответствии с информацией в vsct-файлы.  
  
## <a name="best-practices-for-all-command-sets"></a>Советы и рекомендации для всех наборов команд  
 Для каждого набора команд придерживайтесь следующих рекомендаций.  
  
-   Заранее Подготовьте диаграмму структура команды. Определите команды, поля со списком, группы команд и контекстные меню, которые будут использоваться в нескольких местах.  
  
-   Команды, которые отображаются в той же группе должен быть связан.  
  
-   Группы, содержащие только одной команды являются допустимыми.  
  
-   Пакеты не следует добавлять множество команд существующих меню Visual Studio. Вместо этого они должны создать меню и подменю для размещения новых команд.  
  
-   При поместить команду в существующие меню имя команды, чтобы его назначение было понятно и не следует путать с существующих команд.  
  
## <a name="best-practices-for-small-command-sets"></a>Советы и рекомендации для наборов небольших команд  
 Если вы разрабатываете VSPackage, который имеет лишь несколько команд, также необходимо выполните следующее:  
  
-   По возможности используйте [родительского элемента](../../extensibility/parent-element.md) команды, поле со списком, группу или дочернего меню, чтобы поместить его в соответствующую группу.  
  
-   Назначьте эти группы меню, отображаемых в VSPackage.  
  
-   Должен быть родительским для дочернего меню или команды [элемент группы](../../extensibility/group-element.md). Назначать группам дочернего меню и команд, а затем назначьте группы в родительском меню.  
  
-   Команду можно поместить в дополнительные группы, добавив [элемент CommandPlacements](../../extensibility/commandplacements-element.md) статьи после определения команды, а затем добавляются к `CommandPlacements Element` [CommandPlacement элемент](../../extensibility/commandplacement-element.md) для каждой дополнительной группы.  
  
## <a name="best-practices-for-large-command-sets"></a>Советы и рекомендации для наборов больших команд  
 Если VSPackage будет иметь многие команды, которые будут отображаться в нескольких контекстах, также необходимо выполните следующее:  
  
-   Сделать меню, групп и команд самостоятельно родительские связи. То есть, не назначайте `Parent Element` в определении элемента.  
  
-   Используйте `CommandPlacement Element` записей в `CommandPlacements Element` раздел, чтобы поместить в их родительском меню и группы меню, групп и команд.  
  
-   В `CommandPlacements` статьи, операции, которые заполнения данного меню или группа должны иметь рядом друг с другом. Это помогает читаемость и делает `Priority` проще определить приоритеты.  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Таблицы команд Visual Studio (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
