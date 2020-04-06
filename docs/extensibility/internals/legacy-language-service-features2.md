---
title: Особенности Устаревшей Языковой Службы2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33f12e816476aa54f334988b99b9e86e820784f6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707374"
---
# <a name="legacy-language-service-features"></a>Функции языковой службы прежних версий
Ниже приведены следующие темы, некоторые из устаревших функций языковой службы, которые вы можете предоставить.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше о новом способе реализации языковой [службы,](../../extensibility/editor-and-language-service-extensions.md)см.

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="in-this-section"></a>В этом разделе
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Объясняет, как реализовать окраску синтаксиса.

- [Автоматическое форматирование в языковой службе прежних версий](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Объясняет, как реализовать автоматическое форматирование.

- [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Объясняет, как реализовать IntelliSense Параметр Информация Инструмент.

- [Завершение операторов в языковой службе прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Объясняет, как реализовать список заявлений IntelliSense и список завершения участников.

- [Структурирование и скрытый текст в языковой службе прежних версий](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Объясняет, как реализовать сизложенную или скрытый текст.

- [Практическое руководство. Расширенная поддержка структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Объясняет некоторые шаги в реализации поддержки отладчиков.

## <a name="related-sections"></a>Связанные разделы
