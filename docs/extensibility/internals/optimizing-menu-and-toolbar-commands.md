---
title: Оптимизация команд меню и панелей инструментов | Документация Майкрософт
description: Узнайте, как в Visual Studio можно максимально сокращать путаницу в команде, выполнив Добавление пакетов VSPackage и соответствующих команд.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b35f3a87f819885685b54888031883f4c2776d04
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877602"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Оптимизация команд меню и панелей инструментов
Добавление пакетов VSPackage и соответствующих им команд [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] может привести к переполнению пользовательского интерфейса. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляет способы, позволяющие сократить путаницу в команде пользовательского интерфейса.

## <a name="in-this-section"></a>В этом разделе
- [Как сделать команды доступными](../../extensibility/internals/making-commands-available.md)

 Содержит общие рекомендации по минимизации кровдинг [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса при добавлении пакетов VSPackage.

- [Рекомендации по размещению](../../extensibility/internals/command-placement-guidelines.md)

 Содержит конкретные рекомендации по реализации пакета VSPackage в соответствии с размером набора команд.

## <a name="related-sections"></a>Связанные разделы
- [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.
