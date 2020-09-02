---
title: Маршрутизация команд в пакетах VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 957ddcca46365a882609c15c96d666c2848ace6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709559"
---
# <a name="command-routing-in-vspackages"></a>Маршрутизация команд в пакетах VSPackage
Команда направляется в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] зависимости от контекста, в котором она выполняется. Он направляется от первоначального контекста к глобальному контексту.

## <a name="in-this-section"></a>В этом разделе
- [Алгоритм маршрутизации команд](../../extensibility/internals/command-routing-algorithm.md)

 Описывает порядок разрешения маршрутизации команд.

- [Доступность команды](../../extensibility/internals/command-availability.md)

 Обсуждается маршрутизация команд.

- [Команды и меню, использующие сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Обсуждаются вопросы в командах маршрутизации между управляемым кодом и COM.

## <a name="related-sections"></a>Связанные разделы
- [Объекты контекста выделения](../../extensibility/internals/selection-context-objects.md)

 Обсуждается модель того, как можно определить фокус контекста выбора пользователя в окне.

- [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.
