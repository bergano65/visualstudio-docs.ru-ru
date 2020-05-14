---
title: Элементы проектирования управления источниками VSPackage (ru) Документы Майкрософт
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
ms.openlocfilehash: b5e94829f781c058d9b0ea56cdec6c03c71ffe0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704999"
---
# <a name="source-control-vspackage-design-elements"></a>Элементы проектирования пакета VSPackage системы управления версиями
Темы в этом разделе излагают структуру, которую должен реализовать управление исходным источником VSPackage для глубокой интеграции. В нем также перечислены интерфейсы и службы, которые может реализовать элементуправления исходного кода [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage, а также интерфейсы и службы, которые VSPackage может использовать из других компонентов для поддержки модели управления исходным сообщением и функциональности.

## <a name="in-this-section"></a>В этом разделе
- [Структура VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Определяет структуру управления исходом VSPackage.

- [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Списки интерфейсов и служб, связанных с пакетом управления исходным элементом.

- [Предоставленные службы](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Описывает услугу управления исходным сообщением, предоставляемую управлением исходным источником VSPackage.

## <a name="related-sections"></a>Связанные разделы
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Обсуждается, как создать элемент управления исходным элементом VSPackage, который не [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] только поставляет функциональность управления исходным источником, но и может быть использован для настройки uI управления исходным управлением.
