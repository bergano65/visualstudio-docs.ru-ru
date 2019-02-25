---
title: Элементы проектирования пакета VSPackage управления источника | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e10825bb9bc9659728fbaaeb023a595745b7bcd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642707"
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