---
title: Особенности управления источниками VSPackage (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a01b9d8fbf5f8d0645b5245d21b05aba9e7dacea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705016"
---
# <a name="source-control-vspackage-features"></a>Функции пакета VSPackage системы управления версиями
В этом разделе описаны различные особенности управления исходным элементом VSPackage. В нем излагаются детали регистрации и выбора для такого VSPackage, а также рассматриваются три основные функции управления исходным элементом: обработка событий query-Edit Query-Save, замена глифов и пользовательский пользовательский интерфейс (UI) для функций управления исходным интерфейсом.

## <a name="in-this-section"></a>В этом разделе
- [Регистрация и выбор](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Описывает механизмы регистрации и отбора пакетов.

- [Изменение запроса / сохранение запроса](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Объясняет роль событий query-Edit Query-Save и то, как они обрабатываются диспетчером исходного кода VSPackage.

- [Управление глифами](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Описывает уровни контроля глифов и способы их реализации.

- [Настраиваемый пользовательский](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Излагается элементы uI, которые может указать элементы управления исходным элементом VSPackage.

## <a name="related-sections"></a>Связанные разделы
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Обсуждается, как создать элемент управления исходным элементом VSPackage, который не [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] только поставляет функциональность управления исходным источником, но и может быть использован для настройки uI управления исходным управлением.
