---
title: Оптимизация меню и команды панели инструментов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c76e4f37fd77bd35526153bd86d419417a6cdb6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333130"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Оптимизация команд меню и панелей инструментов
Добавление пакетов VSPackage и их соответствующие команды, чтобы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] может привести к загромождению пользовательского интерфейса. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет способы путаницы пользовательского интерфейса команды.

## <a name="in-this-section"></a>В этом разделе
- [Как сделать команды доступными](../../extensibility/internals/making-commands-available.md)

 Приводятся общие рекомендации по минимизации частенько получает сильнейший из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса при добавлении пакетов VSPackage.

- [Рекомендации по размещению](../../extensibility/internals/command-placement-guidelines.md)

 Предоставляет конкретные рекомендации для реализации VSPackage в соответствии с размером набора команд.

## <a name="related-sections"></a>Связанные разделы
- [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.