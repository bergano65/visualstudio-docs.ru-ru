---
title: Компоненты VSPackage системы управления версиями | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705016"
---
# <a name="source-control-vspackage-features"></a>Функции пакета VSPackage системы управления версиями
В этом разделе описаны различные возможности пакета VSPackage системы управления версиями. В нем описаны сведения о регистрации и выборе для такого пакета VSPackage, а также обсуждаются три основных функции, связанные с управлением исходным кодом: обработка событий запросов, операций сохранения (QEQS), замена глифов и настраиваемый пользовательский интерфейс для функций управления версиями.

## <a name="in-this-section"></a>в этом разделе
- [Регистрация и выбор](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

 Описывает механизмы регистрации и выбора пакетов.

- [Изменение запроса / сохранение запроса](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

 Объясняется роль запроса на изменение запроса и сохранение событий, а также их обработка с помощью пакета VSPackage системы управления версиями.

- [Управление глифами](../../extensibility/internals/glyph-control-source-control-vspackage.md)

 Описывает уровни элемента управления глифами и способы их реализации.

- [Настраиваемый пользовательский](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

 Описывает элементы пользовательского интерфейса, которые может указывать пакет VSPackage для управления версиями.

## <a name="related-sections"></a>См. также
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Описывает, как создать пакет VSPackage системы управления версиями, который не только обеспечивает функциональность управления версиями, но и может использоваться для настройки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса системы управления версиями.
