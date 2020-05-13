---
title: Расширение меню и команд (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711799"
---
# <a name="extend-menus-and-commands"></a>Расширить меню и команды
Команды - это способ добавления действий и процессов в Visual Studio. В большинстве случаев команды отображаются в меню или панели инструментов. Шаблон проекта VSPackage показывает, как реализовать очень основную команду. Для немного более длительной, но все еще базовой реализации [см. Создать расширение с командой меню.](../extensibility/creating-an-extension-with-a-menu-command.md)

 Для получения дополнительной информации о командах, меню и панели инструментов Visual Studio [см.](../extensibility/internals/commands-menus-and-toolbars.md)

 Команды, меню и панели инструментов определяются в файле *.vsct,* который является частью проектов VSPackage. Вы можете найти информацию о Visual Studio IDE и *файле .vsct* в [Как VSPackages добавить элементы пользовательского интерфейса.](../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Ниже приведены темы, объясняющие, как добавлять различные виды команд, меню и панели инструментов.

## <a name="in-this-section"></a>В этом разделе
- [Добавьте меню в панель меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Объясняет, как добавить меню в верхний бар меню Visual Studio.

- [Привязать ярлыки клавиатуры к элементам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Объясняет, как добавить ярлык клавиатуры (например, CTRL No 3) в пункт меню.

- [Добавить подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md) Объясняет, как добавить подменю в верхнее меню.

- [Добавьте самый последний использованный список в подменю](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Объясняет, как добавить список самых последних случаев.

- [Создание многоразовых групп кнопок](../extensibility/creating-reusable-groups-of-buttons.md) Описывает, как группировать элементы команд, чтобы они могли быть включены в несколько меню.

- [Добавление значков в команды меню](../extensibility/adding-icons-to-menu-commands.md) Описывает, как добавить значок в команду как на панели инструментов, так и в меню.

- [Изменить текст команды меню](../extensibility/changing-the-text-of-a-menu-command.md) Описывает использование `TextChanges` флага для динамического изменения элемента меню.

- [Изменение внешнего вида команды](../extensibility/changing-the-appearance-of-a-command.md) Описывает, как динамически включить или отключить команду.

- [Обновление пользовательского интерфейса](../extensibility/updating-the-user-interface.md) Описывает, как заставить обновление пользовательского интерфейса отражать последние изменения.

- [Локализация команд меню](../extensibility/localizing-menu-commands.md) Объясняет, как локализовать команды меню.
