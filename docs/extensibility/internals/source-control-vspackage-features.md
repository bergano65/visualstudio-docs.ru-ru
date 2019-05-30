---
title: Источник функции управления пакета VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 513f43787040075ea0904c97b1aca9866359520a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322496"
---
# <a name="source-control-vspackage-features"></a>Функции пакета VSPackage системы управления версиями
В этом разделе описываются различные функции из пакета VSPackage системы управления версиями. Здесь указаны регистрации и выбора, подробные данные об таких VSPackage, а также рассматриваются три функций управления, связанных с основным источником: обработка событий запроса сохранить изменения запроса (QEQS), замену глифов и настраиваемый пользовательский интерфейс (UI) для системы управления версиями функции.

## <a name="in-this-section"></a>В этом разделе
- [Регистрация и выбор](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Описываются механизмы регистрации и выбора пакета.

- [Изменение запроса / сохранение запроса](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Поясняется в запрос изменения запроса сохранения событий и как они обрабатываются элементом управления источником VSPackage.

- [Управление глифами](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Описание уровней управления глифа и способы их реализации.

- [Настраиваемый пользовательский](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Описываются элементы пользовательского интерфейса, которые можно указать пакет VSPackage системы управления версиями.

## <a name="related-sections"></a>Связанные разделы
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Описывает, как создать пакет VSPackage, который не только предоставляет функции системы управления версиями, но можно использовать для настройки системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] система управления версиями пользовательского интерфейса.