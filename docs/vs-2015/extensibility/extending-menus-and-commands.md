---
title: Расширение меню и команд | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83d9dc45863f1ed1b5e11c17b9e922b62b0186dc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204522"
---
# <a name="extending-menus-and-commands"></a>Расширение меню и команд
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Команды можно добавить действия и процессов в Visual Studio. В большинстве случаев команды отображаются в меню и панелей инструментов. Шаблон проекта VSPackage показан способ реализации очень простой команды. Немного больше времени, но по-прежнему простую реализацию, см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Дополнительные сведения о командах, меню и панелей инструментов Visual Studio, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Команды, меню и панелей инструментов определяются в vsct-файл, который является частью проектов VSPackage. Можно найти сведения об интегрированной среде разработки Visual Studio и vsct-файл в [как пакеты VSPackage добавить элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Как добавить различные команды, меню и панелей инструментов в следующих разделах.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Добавление меню в строку меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 В этой статье описывается добавление меню в верхней строке меню Visual Studio.  
  
 [Привязка сочетаний клавиш к пунктам меню](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Объясняется, как добавить сочетание клавиш (например, CTRL + 3) для пункта меню.  
  
 [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)  
 В этой статье описывается добавление подменю в верхнем меню.  
  
 [Добавление недавно используемого списка в подменю](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Объясняется, как добавить список последних использовавшихся.  
  
 [Создание повторно используемых групп кнопок](../extensibility/creating-reusable-groups-of-buttons.md)  
 Описывает, как группировать элементы команды, таким образом, чтобы их можно было добавлять в нескольких меню.  
  
 [Добавление значков в команды меню](../extensibility/adding-icons-to-menu-commands.md)  
 В этой статье описывается добавление значка для команды на панели инструментов и меню.  
  
 [Изменение текста команды меню](../extensibility/changing-the-text-of-a-menu-command.md)  
 Описание использования `TextChanges` флаг, включающий элемент меню, чтобы динамически изменяться.  
  
 [Изменение внешнего вида команды](../extensibility/changing-the-appearance-of-a-command.md)  
 Описывает, как динамически включить или отключить команду.  
  
 [Обновление пользовательского интерфейса](../extensibility/updating-the-user-interface.md)  
 Описывает, как выполнить принудительное обновление пользовательского интерфейса для отображения последних изменений.  
  
 [Локализация команд меню](../extensibility/localizing-menu-commands.md)  
 Объясняется, как локализация команд меню.  
  
## <a name="related-sections"></a>Связанные разделы
