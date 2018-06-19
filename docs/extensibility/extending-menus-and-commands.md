---
title: Расширение меню и команд | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 830748be6f2cedf57b94a9824bc0912820067718
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128036"
---
# <a name="extending-menus-and-commands"></a>Расширение меню и команд
Команды, способ добавления действий и процессов в Visual Studio. В большинстве случаев команды отображаются в меню или панели инструментов. Шаблон проекта VSPackage показан способ реализации очень простой команды. Немного больше времени, но по-прежнему простую реализацию, см. [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Дополнительные сведения о командах, меню и панели инструментов Visual Studio см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Команды, меню и панелей инструментов определяются в vsct-файле, который является частью проектов VSPackage. Можно найти сведения об Интегрированной среде разработки Visual Studio и vsct-файл в [как пакеты VSPackage добавить элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Следующие разделы описывают добавить различные команды, меню и панели инструментов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Добавление меню в строку меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Объясняет, как добавить меню в верхней строке меню Visual Studio.  
  
 [Привязка сочетаний клавиш к пунктам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Объясняется, как добавить сочетание клавиш (например, CTRL + 3) для пункта меню.  
  
 [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)  
 В этой статье описывается добавление подменю в верхнем меню.  
  
 [Добавление недавно используемого списка в подменю](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Объясняет, как добавить список последних использовавшихся.  
  
 [Создание повторно используемых групп кнопок](../extensibility/creating-reusable-groups-of-buttons.md)  
 Описывает способ группировки элементов команды, чтобы их можно включить в несколько меню.  
  
 [Добавление значков в команды меню](../extensibility/adding-icons-to-menu-commands.md)  
 Описывает, как добавить значок для команды на панели инструментов и меню.  
  
 [Изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md)  
 Описывает использование `TextChanges` флаг, включающий пункт меню, чтобы динамически изменяться.  
  
 [Изменение внешнего вида команды](../extensibility/changing-the-appearance-of-a-command.md)  
 Описывает, как динамически включить или отключить команду.  
  
 [Обновление пользовательского интерфейса](../extensibility/updating-the-user-interface.md)  
 Описывает, как выполнить принудительное обновление пользовательского интерфейса для отображения последних изменений.  
  
 [Локализация команд меню](../extensibility/localizing-menu-commands.md)  
 Описание способов локализации команды меню.  
  
## <a name="related-sections"></a>Связанные разделы