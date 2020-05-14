---
title: Начало работы с Рослин Анализаторы (ru) Документы Майкрософт
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711271"
---
# <a name="get-started-with-roslyn-analyzers"></a>Начало работы с анализаторов Roslyn

С помощью анализаторов кода на основе проектов в Visual Studio авторы API могут поставлять анализ кода, специфичный для доменов, как часть своих пакетов NuGet. Поскольку эти анализаторы питаются от платформы компиляторов .NET (кодовое название "Roslyn"), они могут создавать предупреждения в коде при вводе еще до того, как вы закончите строку (больше не ждать, чтобы построить код, чтобы обнаружить проблемы). Анализаторы могут также поверхности автоматического кода исправить через Visual Studio лампочка подсказка, чтобы позволить вам очистить ваш код немедленно.

## <a name="get-started"></a>Начало работы

[Обзор анализаторов Рослин](../code-quality/roslyn-analyzers-overview.md)

[Руководство. Создание анализатора и исправления кода](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Добавление кодов исправления Walkthrough: Предоставление пользователям исправлений для анализатора проблем](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Реальный мир Рослин анализатор,](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) который вы также можете смотреть, как [говорить](https://channel9.msdn.com/events/Build/2015/3-725)

[Несколько примеров на GitHub, сгруппированных в три вида анализаторов](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>См. также

- [Ссылка на пакет пакетов платформы компилятора .NET](roslyn-version-support.md)
- [Другие документы на сайте GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Правила FxCop, реализованные с помощью анализаторов Roslyn](../code-quality/fxcop-rule-port-status.md)
