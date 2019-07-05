---
title: Команда маршрутизации в пакетах VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a534a015f57a738ca65895002a6fec4454f0ae97
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342228"
---
# <a name="command-routing-in-vspackages"></a>Маршрутизация команд в пакеты VSPackage
Команда направляется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] на основе контекста, в котором он выполняется. Он направляется из исходного контекста наружу в глобальном контексте.

## <a name="in-this-section"></a>Содержание раздела
- [Алгоритм маршрутизации команд](../../extensibility/internals/command-routing-algorithm.md)

 Описывает порядок маршрутизации выполнения команды.

- [Доступность команд](../../extensibility/internals/command-availability.md)

 Описание маршрутизации команд.

- [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Рассматриваются особенности маршрутизированию команд между управляемым кодом и COM.

## <a name="related-sections"></a>Связанные разделы
- [Объекты контекста выбора](../../extensibility/internals/selection-context-objects.md)

 Обсуждается модель для как можно определить пользователя Выбор контекста фокус на окно.

- [Команды, меню и панелей инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.