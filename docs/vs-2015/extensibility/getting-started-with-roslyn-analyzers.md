---
title: Начало работы с Рослин Анализаторы (ru) Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444988"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Начало работы с анализаторами Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью анализаторов кода на основе проектов в Visual Studio авторы API могут поставлять анализ кода, специфичный для доменов, как часть своих пакетов NuGet.  Поскольку эти анализаторы питаются от платформы компиляторов .NET (кодовое название "Roslyn"), они могут создавать предупреждения в коде при вводе еще до того, как вы закончите строку (больше не ждать, чтобы построить код, чтобы обнаружить проблемы).  Анализаторы могут также поверхности автоматического кода исправить через Visual Studio лампочка подсказка, чтобы позволить вам очистить ваш код немедленно

## <a name="getting-started"></a>Приступая к работе
[Рослин Live анализаторы кода Введение и прохождение](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Добавление кода исправления Пошаговая: Предоставить пользователям исправления для анализатора вопросов](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Введение и прохождение реального мира анализатор Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Реальный мир Рослин анализатор,](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) который вы также можете смотреть, как [говорить](https://channel9.msdn.com/events/Build/2015/3-725)

[Несколько примеров на GitHub, сгруппированных в три вида анализаторов](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Введение и тур несколько анализаторов Talk](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Другие ресурсы
[Другие документы на сайте GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Правила FxCop реализованы с помощью анализаторов Roslyn на GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
