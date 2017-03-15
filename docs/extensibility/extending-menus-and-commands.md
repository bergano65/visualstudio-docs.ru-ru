---
title: "Расширение меню и команд | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "меню, общие задачи"
  - "Пакеты VSPackage, задачи меню"
  - "vsct-файлы, общие задачи меню"
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 49
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 49
---
# Расширение меню и команд
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Команды, способ добавления действий и процессов в Visual Studio. В большинстве случаев команды отображаются в меню или панели инструментов. Шаблон проекта VSPackage показан способ реализации очень простой команды. Немного больше времени, но по\-прежнему простую реализацию, в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Дополнительные сведения о командах, меню и панели инструментов Visual Studio см. в разделе [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 В файле .vsct, который является частью VSPackage проекты определенных команд, меню и панели инструментов. Можно найти сведения об Интегрированной среде разработки Visual Studio и файл .vsct в [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Следующие разделы описывают добавить различные команды, меню и панели инструментов.  
  
## В этом подразделе  
 [Добавление меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Объясняет, как добавлять меню в верхней строке меню Visual Studio.  
  
 [Привязка сочетания клавиш к пунктам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Описание способов добавления сочетания клавиш \(например, CTRL \+ 3\) для элемента меню.  
  
 [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)  
 Объясняется, как добавить подменю в верхнем меню.  
  
 [Добавление наиболее недавно использовавшегося списка в подменю](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Описание способов добавления списка последних использовавшихся.  
  
 [Создание многократно используемых групп кнопок](../extensibility/creating-reusable-groups-of-buttons.md)  
 Описывает, как группировать элементы команды, чтобы они могут быть включены в нескольких меню.  
  
 [Добавление значков на команды меню](../extensibility/adding-icons-to-menu-commands.md)  
 Описывает добавление значка к команде на панели инструментов и меню.  
  
 [Изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md)  
 Описание использования `TextChanges` флаг для включения пункт меню, чтобы динамически изменяться.  
  
 [Изменение внешнего вида команды](../extensibility/changing-the-appearance-of-a-command.md)  
 Описывает, как динамически включить или отключить команду.  
  
 [Обновление пользовательского интерфейса](../extensibility/updating-the-user-interface.md)  
 Описывает, как выполнить принудительное обновление пользовательского интерфейса для отображения последних изменений.  
  
 [Локализация команды меню](../extensibility/localizing-menu-commands.md)  
 Описание способов локализации команды меню.  
  
## Связанные подразделы