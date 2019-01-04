---
title: Расширение меню и команд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ef32dd2bbc44f784a2faaf6edcafcba96a8f113
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910494"
---
# <a name="extend-menus-and-commands"></a>Расширение меню и команд
Команды можно добавить действия и процессов в Visual Studio. В большинстве случаев команды отображаются в меню и панелей инструментов. Шаблон проекта VSPackage показан способ реализации очень простой команды. Немного больше времени, но по-прежнему простую реализацию, см. в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Дополнительные сведения о командах, меню и панелей инструментов Visual Studio, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Команды, меню и панелей инструментов определяются в *.vsct* файл, который является частью проектов VSPackage. Можно найти сведения об интегрированной среде разработки Visual Studio и *.vsct* файл [как пакеты VSPackage добавить элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Как добавить различные команды, меню и панелей инструментов в следующих разделах.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Добавить меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 В этой статье описывается добавление меню в верхней строке меню Visual Studio.  
  
 [Привязка сочетания клавиш к пунктам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Объясняется, как добавить сочетание клавиш (например, CTRL + 3) для пункта меню.  
  
 [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)  
 В этой статье описывается добавление подменю в верхнем меню.  
  
 [Добавление недавно использовавшийся списка в подменю](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Объясняется, как добавить список последних использовавшихся.  
  
 [Создание повторно используемых групп кнопок](../extensibility/creating-reusable-groups-of-buttons.md)  
 Описывает, как группировать элементы команды, таким образом, чтобы их можно было добавлять в нескольких меню.  
  
 [Добавление значков для команды меню](../extensibility/adding-icons-to-menu-commands.md)  
 В этой статье описывается добавление значка для команды на панели инструментов и меню.  
  
 [Изменить текст команды меню](../extensibility/changing-the-text-of-a-menu-command.md)  
 Описание использования `TextChanges` флаг, включающий элемент меню, чтобы динамически изменяться.  
  
 [Изменение внешнего вида команды](../extensibility/changing-the-appearance-of-a-command.md)  
 Описывает, как динамически включить или отключить команду.  
  
 [Обновить пользовательский интерфейс](../extensibility/updating-the-user-interface.md)  
 Описывает, как выполнить принудительное обновление пользовательского интерфейса для отображения последних изменений.  
  
 [Локализация команд меню](../extensibility/localizing-menu-commands.md)  
 Объясняется, как локализация команд меню.  