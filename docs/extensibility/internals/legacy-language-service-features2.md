---
title: Устаревшая языковая служба Features2 | Документация Майкрософт
description: Узнайте о некоторых функциях языковой службы прежних версий, которые можно предоставить с помощью расширений Managed Extensibility Framework (MEF) в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: afba05f2dd51dbdcdfcbc155077cb28259888738
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839642"
---
# <a name="legacy-language-service-features-2"></a>Функции языковой службы прежних версий 2
В следующих разделах перечислены некоторые возможности устаревшей языковой службы, которые вы можете предоставить.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации языковой службы см. в статье [расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="in-this-section"></a>В этом разделе
- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Объясняет, как реализовать цветовое выделение синтаксиса.

- [Автоматическое форматирование в языковой службе прежних версий](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 Объясняет, как реализовать автоматическое форматирование.

- [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Объясняет, как реализовать подсказку о параметрах IntelliSense.

- [Завершение операторов в языковой службе прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Объясняет, как реализовать список инструкций IntelliSense и список завершения элементов.

- [Структурирование и скрытый текст в языковой службе прежних версий](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 Описывает, как реализовать структурирование или скрытый текст.

- [Практическое руководство. Расширенная поддержка структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Описание некоторых действий по реализации поддержки отладчика.

## <a name="related-sections"></a>Связанные разделы
