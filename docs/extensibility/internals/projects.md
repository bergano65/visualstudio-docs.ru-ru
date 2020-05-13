---
title: Проекты Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706216"
---
# <a name="projects"></a>Проекты
В Visual Studio проекты — это контейнеры, которые разработчики используют для организации файлов исходного кода и других ресурсов, которые отображаются в **Solution Explorer.** Как правило, проекты — это файлы (например, файл .csproj для проекта C'), которые хранят ссылки на файлы исходного кода и ресурсы, такие как файлы bitmap. Проекты позволяют организовывать, создавать, отлаживать и развертывать исходный код, ссылки на web-службы и базы данных и другие ресурсы. VSPackages может расширить систему проектов Visual Studio тремя основными способами: *типы проектов,* *подтипы проекта*и *пользовательские инструменты.*

## <a name="in-this-section"></a>В этом разделе
- [Типы проектов](../../extensibility/internals/project-types.md)

 *Типы проектов* добавляют поддержку новым видам проектов, таким как языки программирования. Например, каждый язык, который поддерживает Visual Studio, имеет свой собственный тип проекта, а пример интеграции IronPython включает тип проекта для языка IronPython. Необходимо создать тип проекта для языков, не втомую, помимо C- или Visual Basic, чтобы настроить настройку элементов, которые создаются, отлаживаются, развертываются и отображаются в **Solution Explorer.** Для получения дополнительной информации [см.](../../extensibility/internals/project-types.md)

- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)

 *Подтипы проектов* основаны на типах проектов и могут использоваться для настройки способа построения, отладки и развертывания проектов. Visual Studio использует подтипы проектов с проектами Smart Device; они настраивают развертывание, копируя недавно построенную программу с компьютера разработки на целевое устройство. Типы проектов «С» и «Визуальные основы» могут быть использованы в качестве основы для подтипов проектов; Типы проектов СЗ не могут. Ваши собственные типы проектов также могут быть использованы в качестве основы для подтипов проектов. Для получения дополнительной информации [см.](../../extensibility/internals/project-subtypes.md)

- [Веб-проекты](../../extensibility/internals/web-projects.md)

 Объясняет веб-проект, который, в свою очередь, создает веб-приложения.

- [Новое поколение проекта: под капотом, часть первая](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) и [новое поколение проекта: Под капотом, часть вторая](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Объясняет, что происходит на самом деле при создании нового проекта.

- [Образцы VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Содержит образцы в VSSDK, которые касаются проектов и решений.

## <a name="related-sections"></a>Связанные разделы
- [Компоненты пакета SDK для Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Объясните различные аспекты расширяемости Visual Studio.
