---
title: Элементы проектирования пакета VSPackage управления источника | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e9b22ea32698d6e996bfee618b0b5ca4da5943d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322484"
---
# <a name="source-control-vspackage-design-elements"></a>Элементы проектирования пакета VSPackage системы управления версиями
В подразделах этого раздела представления структуры системы управления версиями, которые VSPackage должен реализовать для глубокой интеграции. В ней также перечислены интерфейсы и службы, что система управления VSPackage могут реализовывать интерфейсы и служб VSPackage системы управления версиями можно использовать из других [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компоненты для поддержки источника управлять модели и работой.

## <a name="in-this-section"></a>В этом разделе
- [Структура VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Определяет структуру пакета VSPackage системы управления версиями.

- [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Перечислены интерфейсы, связанные с пакетом управления для источника и служб.

- [Предоставленные службы](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Описание службы управления версиями, предоставляемых VSPackage системы управления версиями.

## <a name="related-sections"></a>Связанные разделы
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Описывает, как создать пакет VSPackage, который не только предоставляет функции системы управления версиями, но можно использовать для настройки системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] система управления версиями пользовательского интерфейса.