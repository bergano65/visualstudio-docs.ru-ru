---
title: Включение или установка анализаторов .NET
ms.date: 08/03/2018
description: Узнайте, как включить анализаторы .NET из пакета SDK для .NET или установить эти анализаторы как пакет NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a14d89caba498a07c2447f9df1109e4da9f6a466
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112189"
---
# <a name="enable-or-install-net-analyzers"></a>Включение или установка анализаторов .NET

## <a name="overview"></a>Обзор

Анализаторы .NET Compiler Platform (Roslyn) проверяют качество кода C# или Visual Basic и выявляют в нем проблемы. Включить или установить эти анализаторы можно одним из следующих способов.

- **Включение из пакета SDK для .NET**: начиная с Visual Studio 2019 16,8 и .NET 5,0, эти анализаторы [входят в состав пакета SDK для .NET](/dotnet/fundamentals/code-analysis/overview). По умолчанию для проектов, предназначенных для .NET 5,0 или более поздней версии, включен анализ. Вы можете включить анализ кода для проектов, предназначенных для более ранних версий .NET, задав `EnableNETAnalyzers` для свойства значение `true` . Можно также отключить анализ кода для проекта, задав для значение `EnableNETAnalyzers` `false` .

- **Установить как пакет NuGet**. можно также установить эти анализаторы, установив `Microsoft.CodeAnalysis.NetAnalyzers` [пакет NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) в Visual Studio 2019. Если вы используете Visual Studio 2017, установите последнюю `2.9.x` версию `Microsoft.CodeAnalysis.FxCopAnalyzers` [пакета NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> Рекомендуется включить анализаторы из пакета SDK для .NET, а не устанавливать `Microsoft.CodeAnalysis.NetAnalyzers` [пакет NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), если это возможно. При включении анализаторов из пакета SDK для .NET автоматически получаются исправления ошибок анализатора и новые анализаторы, как только вы обновите пакет SDK.

## <a name="see-also"></a>См. также раздел

- [Обзор анализаторов кода в Visual Studio](roslyn-analyzers-overview.md)
- [Использование анализаторов кода в Visual Studio](use-roslyn-analyzers.md)
- [Миграция из устаревшего анализа в анализаторы .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Миграция с FxCop Analyzer на анализаторы .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
