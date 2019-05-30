---
title: Расширение меню и команд | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0810e1fde5b58416b94607dccf2004fe7edb67b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341139"
---
# <a name="extend-menus-and-commands"></a>Расширение меню и команд
Команды можно добавить действия и процессов в Visual Studio. В большинстве случаев команды отображаются в меню и панелей инструментов. Шаблон проекта VSPackage показан способ реализации очень простой команды. Немного больше времени, но по-прежнему простую реализацию, см. в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

 Дополнительные сведения о командах, меню и панелей инструментов Visual Studio, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).

 Команды, меню и панелей инструментов определяются в *.vsct* файл, который является частью проектов VSPackage. Можно найти сведения об интегрированной среде разработки Visual Studio и *.vsct* файл [как пакеты VSPackage добавить элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Как добавить различные команды, меню и панелей инструментов в следующих разделах.

## <a name="in-this-section"></a>Содержание раздела
- [Добавить меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) объясняет, как добавить меню в верхней строке меню Visual Studio.

- [Привязка сочетания клавиш к пунктам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) объясняется, как добавить сочетание клавиш (например, CTRL + 3) для пункта меню.

- [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md) описывается добавление подменю в верхнем меню.

- [Добавить список недавно использовавшихся в подменю](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) объясняется, как добавить список последних использовавшихся.

- [Создание повторно используемых групп кнопок](../extensibility/creating-reusable-groups-of-buttons.md) описывается, как группировать элементы команды, таким образом, чтобы их можно было добавлять в нескольких меню.

- [Добавление значков для команды меню](../extensibility/adding-icons-to-menu-commands.md) описывается, как добавить значок для команды на панели инструментов и меню.

- [Изменить текст команды меню](../extensibility/changing-the-text-of-a-menu-command.md) описывается использование `TextChanges` флаг, включающий элемент меню, чтобы динамически изменяться.

- [Изменение внешнего вида команды](../extensibility/changing-the-appearance-of-a-command.md) описывается, как динамически включить или отключить команду.

- [Обновить пользовательский интерфейс](../extensibility/updating-the-user-interface.md) описана реализация принудительного обновления пользовательского интерфейса для отображения последних изменений.

- [Локализация команд меню](../extensibility/localizing-menu-commands.md) объясняется, как локализация команд меню.