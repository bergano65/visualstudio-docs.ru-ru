---
title: Элементы проектирования VSPackage в системе управления версиями | Документация Майкрософт
description: Сведения о структуре, которую должен реализовать пакет VSPackage системы управления версиями, а также интерфейсы и службы, которые может реализовать пакет VSPackage системы управления версиями.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e586470208989dce070c92963fc215f1053559a4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877654"
---
# <a name="source-control-vspackage-design-elements"></a>Элементы проектирования пакета VSPackage системы управления версиями
В подразделах этого раздела описывается структура, которую должен реализовать пакет VSPackage системы управления версиями для глубокой интеграции. В нем также перечислены интерфейсы и службы, которые может реализовать пакет VSPackage системы управления версиями, а также интерфейсы и службы, которые пакет VSPackage может использовать из других [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компонентов для поддержки модели и функциональности системы управления версиями.

## <a name="in-this-section"></a>В этом разделе
- [Структура VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Определяет структуру пакета VSPackage системы управления версиями.

- [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Содержит список интерфейсов и служб, связанных с пакетом управления версиями.

- [Предоставленные службы](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Описывает службу управления версиями, предоставляемую пакетом VSPackage системы управления версиями.

## <a name="related-sections"></a>Связанные разделы
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Описывает, как создать пакет VSPackage системы управления версиями, который не только обеспечивает функциональность управления версиями, но и может использоваться для настройки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательского интерфейса системы управления версиями.
