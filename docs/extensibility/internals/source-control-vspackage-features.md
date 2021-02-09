---
title: Компоненты VSPackage системы управления версиями | Документация Майкрософт
description: Сведения о функциях пакета VSPackage системы управления версиями, включая сведения о регистрации и выборе, а также о некоторых основных функциях, связанных с управлением версиями.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, features
ms.assetid: 26c3ffda-22b8-4345-9fb6-2883f37699aa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a29b1b3af1e92ee6f247ba07e3b4e468401415e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895431"
---
# <a name="source-control-vspackage-features"></a>Функции пакета VSPackage системы управления версиями
В этом разделе описаны различные возможности пакета VSPackage системы управления версиями. В нем описаны сведения о регистрации и выборе для такого пакета VSPackage, а также обсуждаются три основных функции, связанные с системой управления версиями: обработка событий Query-Edit Query-Save (QEQS), замена глифов и пользовательский интерфейс (UI) для функций управления версиями.

## <a name="in-this-section"></a>В этом разделе
- [Регистрация и выбор](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Описывает механизмы регистрации и выбора пакетов.

- [Изменение запроса / сохранение запроса](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Описание роли Query-Edit Query-Save событий и их обработки пакетом VSPackage системы управления версиями.

- [Управление глифами](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Описывает уровни элемента управления глифами и способы их реализации.

- [Настраиваемый пользовательский](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Описывает элементы пользовательского интерфейса, которые может указывать пакет VSPackage для управления версиями.

## <a name="related-sections"></a>Связанные разделы
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Описывает, как создать пакет VSPackage системы управления версиями, который не только обеспечивает функциональность управления версиями, но и может использоваться для настройки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса системы управления версиями.
