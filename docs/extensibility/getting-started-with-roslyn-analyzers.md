---
title: начало работы с анализаторами Roslyn | Документация Майкрософт
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21b2d77d8c038988fa77293280c9ff7ad38cc82e
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822339"
---
# <a name="get-started-with-roslyn-analyzers"></a>Начало работы с анализаторами Roslyn

С помощью динамических анализаторов кода, основанных на проектах в Visual Studio, авторы API могут поставлять анализ кода, зависящего от домена, как часть пакетов NuGet. Поскольку эти анализаторы работают на основе .NET Compiler Platform (с кодовым названием «Roslyn»), они могут создавать предупреждения в коде по мере ввода, прежде чем завершить строку (больше не нужно дожидаться сборки кода для обнаружения проблем). Анализаторы также могут выполнять автоматическое исправление кода в командной строке лампочки Visual Studio, чтобы вы могли немедленно выполнить очистку кода.

## <a name="get-started"></a>Начало работы

[Обзор анализаторов Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Учебник. Напишите первый анализатор и исправьте код](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Добавление исправлений кода пошаговое руководство. Предоставление пользователям исправлений для проблем с анализатором](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Roslyn анализатор реального мира](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , который можно также просмотреть в качестве [разговора](https://channel9.msdn.com/events/Build/2015/3-725)

[Несколько примеров на сайте GitHub, сгруппированных в три вида анализаторов](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>См. также

- [Справочник по версии пакета платформы компилятора .NET](roslyn-version-support.md)
- [Дополнительные документы на сайте OSS для GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Правила FxCop, реализованные с анализаторами Roslyn](../code-quality/fxcop-rule-port-status.md)
