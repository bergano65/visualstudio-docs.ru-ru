---
title: Расширяемость устаревшей языковой службы (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707411"
---
# <a name="legacy-language-service-extensibility"></a>Расширяемость языковой службы прежних версий
Языковая служба предоставляет языковую поддержку для редактирования исходного кода в IDE.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше о новом способе реализации языковой [службы,](../../extensibility/editor-and-language-service-extensions.md)см.

 В этом разделе рассматриваются структура и реализация устаревшей языковой службы.

## <a name="in-this-section"></a>В этом разделе
- [Миграция языковой службы прежних версий](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Объясняет, как обновить языковой сервис от Visual Studio 2008 до последней версии.

- [Основные компоненты языковой службы прежних версий](../../extensibility/internals/legacy-language-service-essentials.md)

 Предоставляет важную информацию о том, как развивать языковые службы для интеграции языка программирования в Visual Studio.

- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)

 Предоставляет ссылки на темы, которые могут помочь вам создать языковую службу.

- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Предоставляет информацию о поддержке выделения синтаксиса в языковой службе.

- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Предоставляет информацию о том, как использовать платформу управляемого пакета (MPF) для реализации полнофункциональных языковых услуг в управляемом коде.

- [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Описывает библиотеки и инструменты, позволяющие просматривать виды символов в IDE.

## <a name="related-sections"></a>Связанные разделы
- [Расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md)

 Предоставляет обзор редакторов Visual Studio.

- [Поддержка языковой службы для отладки](../../extensibility/internals/language-service-support-for-debugging.md)

 Предоставляет информацию и ссылку на Visual Studio Debugging SDK, которая содержит информацию, необходимую для создания и настройки компонентов отладки, используемых для отладки программ.
