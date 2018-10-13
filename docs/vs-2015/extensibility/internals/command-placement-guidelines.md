---
title: Рекомендации по размещению команд | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf6c047e649f1615cbb15704621d3c0a8eafaf2e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284887"
---
# <a name="command-placement-guidelines"></a>Рекомендации по размещению команд
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Советы и рекомендации для позиционирования команд в среде разработки Visual Studio (IDE) зависит от размера набора команд. Команды определяются и расположена в соответствии со сведения в vsct-файлы.  
  
## <a name="best-practices-for-all-command-sets"></a>Советы и рекомендации для всех наборов команд  
 Для каждого набора команд придерживайтесь следующих рекомендаций.  
  
-   Заранее Подготовьте план структура команды. Чтобы определите команды, поля со списком, группы команд и контекстных меню, которые будут использоваться в нескольких местах.  
  
-   Команды, которые отображаются в той же группе должен быть связан.  
  
-   Группы, которые содержат только одной команды являются допустимыми.  
  
-   Пакеты не следует добавить большое количество команд в существующие меню Visual Studio. Вместо этого они должны создать меню или подменю для размещения новых команд.  
  
-   При переводе команду на существующее меню, имя команды, чтобы его назначение было понятно, и его не следует путать с помощью существующих команд.  
  
## <a name="best-practices-for-small-command-sets"></a>Советы и рекомендации для наборов небольших команд  
 Если вы разрабатываете пакет VSPackage, который имеет несколько команд, кроме того, придерживайтесь следующих рекомендаций.  
  
-   По возможности используйте [родительского элемента](../../extensibility/parent-element.md) команды, поле со списком, группы или дочернего меню, чтобы поместить его в соответствующую группу.  
  
-   Назначьте эти группы меню, отображаемого элементом VSPackage.  
  
-   Должен быть родительским для дочернего меню или команду [элемент группы](../../extensibility/group-element.md). Команды и дочерних меню назначаются группам, а затем назначить группы родительского меню.  
  
-   Команду можно поместить в дополнительные группы, добавив [элемент CommandPlacements](../../extensibility/commandplacements-element.md) после определения команды, при этом добавляя `CommandPlacements Element` [элемент CommandPlacement](../../extensibility/commandplacement-element.md) для каждого Дополнительные группы.  
  
## <a name="best-practices-for-large-command-sets"></a>Советы и рекомендации для наборов больших команд  
 Если VSPackage будет иметь многие команды, которые будут отображаться в нескольких контекстах, также придерживайтесь следующих рекомендаций.  
  
-   Убедитесь в меню, группы и команды, которые самостоятельно родительские связи. То есть, не назначайте `Parent Element` в определении элемента.  
  
-   Используйте `CommandPlacement Element` записей в `CommandPlacements Element` раздел, чтобы поместить в их родительском меню и группы меню, группы и команды.  
  
-   В `CommandPlacements` разделе записей, которые заполняют меню или группа должны иметь рядом друг с другом. Это также помогает читаемость и делает `Priority` рейтинг само по себе проще определить.  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

