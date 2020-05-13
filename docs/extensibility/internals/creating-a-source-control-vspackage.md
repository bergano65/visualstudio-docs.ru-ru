---
title: Создание управления источником VSPackage (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709194"
---
# <a name="create-a-source-control-vspackage"></a>Создание управления исходным элементом VSPackage
Эта документация содержит ссылки на обзор архитектуры [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]пакета управления исходным управлением, интегрированного с API, который определяется интерфейсами, которые будут реализованы, и служб, которые будут использоваться, и выборку, иллюстрирующую простую реализацию пакета управления исходным управлением.

 С помощью управления исходным элементом VSPackage можно создать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]глубокий путь интеграции для интеграции исходного элемента с . Это позволяет пакету обойти uI управления исходным управлением [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]по умолчанию, размещенный, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отвечать на запросы управления исходными данными из проектной системы и взаимодействовать с такими компонентами, как **Solution Explorer.** Дает [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] партнерам возможность создать VSPackage, который может [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрироваться с помощью модели обслуживания.

## <a name="in-this-section"></a>В этом разделе
- [Начало работы](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 Обсуждаетпакет управления исходным ресурсом, который является более продвинутой альтернативой плагину управления исходным элементом для реализации функций управления исходным источником в. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

- [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)

 Представляет диаграмму и объясняет компоненты пакета управления исходным источником.

- [Компоненты](../../extensibility/internals/source-control-vspackage-features.md)

 Описывает различные особенности пакета управления исходным источником.

- [Элементы дизайна](../../extensibility/internals/source-control-vspackage-design-elements.md)

 Описывает структуру VSPackage, который пакет управления исходным источником должен реализовать для глубокой интеграции.

## <a name="related-sections"></a>См. также
- [Создание плагина управления исходным элементом](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Обсуждается, как создать плагин управления исходным элементом, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] который обеспечивает функциональность управления исходным управлением в пользовательском интерфейсе управления исходным управлением (UI).

- [Управление исходом](../../extensibility/internals/source-control.md)

 Обсуждается варианты реализации управления исходным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]источником в качестве интегрированной функции .
