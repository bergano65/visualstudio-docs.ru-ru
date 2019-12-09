---
title: начало работы с анализаторами Roslyn | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d45491fe031c01a31812f5ed4944f76d059cd60
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300017"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Начало работы с анализаторами Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью динамических анализаторов кода, основанных на проектах в Visual Studio, авторы API могут поставлять анализ кода, зависящего от домена, как часть пакетов NuGet.  Поскольку эти анализаторы работают на основе .NET Compiler Platform (с кодовым названием «Roslyn»), они могут создавать предупреждения в коде по мере ввода, прежде чем завершить строку (больше не нужно дожидаться сборки кода для обнаружения проблем).  Анализаторы также могут выполнять автоматическое исправление кода в командной строке лампочки Visual Studio, чтобы вы могли немедленно очистить код.

## <a name="getting-started"></a>Начало работы
[Введение и пошаговое руководство по Roslyn Live Code Analyzer](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Добавление исправлений кода пошаговое руководство. предоставление пользователям исправлений для проблем с анализатором](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Введение и пошаговое руководство по использованию анализатора реального мира](https://channel9.msdn.com/events/Build/2015/3-725)

[Roslyn анализатор реального мира](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , который можно также просмотреть в качестве [разговора](https://channel9.msdn.com/events/Build/2015/3-725)

[Несколько примеров на сайте GitHub, сгруппированных в три вида анализаторов](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Введение и обзор нескольких анализаторов](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Другие ресурсы
[Дополнительные документы на сайте OSS для GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Правила FxCop, реализованные с анализаторами Roslyn на GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
