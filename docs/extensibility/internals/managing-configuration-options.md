---
title: Управление параметрами конфигурации | Документация Майкрософт
description: Узнайте, как управлять параметрами конфигурации проекта и решения в Visual Studio для управления построением, упаковкой, развертыванием и запуском проекта.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options
ms.assetid: 596c28ee-f48d-4252-a5c4-f730c43a39e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34f772b780cda825861e11e6816d1d88405f74e
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204535"
---
# <a name="managing-configuration-options"></a>Управление параметрами конфигурации
При создании нового типа проекта необходимо управлять параметрами конфигурации проекта и решения, которые определяют, как будет выполняться сборка, упаковка, развертывание и запуск проекта. В следующих разделах рассматривается конфигурация проекта и решения.

## <a name="in-this-section"></a>В этом разделе
- [Обзор](../../extensibility/internals/configuration-options-overview.md)

 Описывает, как проекты в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] могут поддерживать несколько конфигураций.

- [Страницы свойств](../../extensibility/internals/property-pages.md)

 Объясняется, что пользователи могут просматривать и изменять зависимые от конфигурации проекта свойства и независимые свойства с помощью страниц свойств.

- [Конфигурация решения](../../extensibility/internals/solution-configuration.md)

 Содержит сведения о том, что хранится в конфигурациях решений, и о том, как конфигурации решения направляют поведение команд **запуска** и **сборки** .

- [Объект конфигурации проекта](../../extensibility/internals/project-configuration-object.md)

 Объясняет, как объект конфигурации проекта управляет отображением сведений о конфигурации в пользовательском интерфейсе.

- [Конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md)

 Объясняется, как список конфигураций решения для конкретного решения управляется с помощью диалогового окна **конфигурации решения** .

- [Конфигурация проекта для управления развертыванием](../../extensibility/internals/project-configuration-for-managing-deployment.md)

 Определяет действие развертывания и два способа [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддержки проектов, поддерживающих развертывание.

- [Конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)

 Описание процессов сборки, поддерживаемых каждой конфигурацией, а также интерфейсов и методов, с помощью которых можно сделать доступными выходные элементы.

## <a name="related-sections"></a>Связанные разделы
- [Типы проектов](../../extensibility/internals/project-types.md)

 Содержит общие сведения о проектах в качестве основных стандартных блоков [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Имеются ссылки на дополнительные разделы, объясняющие, как проекты управляют сборкой и компиляцией кода.
