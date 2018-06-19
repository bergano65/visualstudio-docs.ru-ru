---
title: Приступая к работе с Roslyn анализаторы | Документы Microsoft
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7b887703343dab10f9cc1f0cbf8e2e2b37b0065b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126813"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Приступая к работе с Roslyn анализаторы

С помощью анализаторов динамической, основанное на проект кода в Visual Studio API авторы могут поставляться анализ кода для конкретного домена как часть своих пакетов NuGet. Поскольку эти анализаторы берутся из платформой компилятора .NET (кодовое название «Roslyn»), они создают предупреждения в коде при вводе еще до завершения строки, (больше не ожидает создания кода для обнаружения проблем). Анализаторы, также могут возникать исправления автоматического кода из строки лампочки Visual Studio позволяет очистить коде немедленно.

## <a name="getting-started"></a>Начало работы

[Динамическая анализаторов Roslyn введение и пошаговое руководство](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Добавление кода устраняет Пошаговое руководство: Предоставления пользователям исправления проблем анализатора](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Общие сведения и пошаговое руководство по Talk анализатора реального мира](http://channel9.msdn.com/events/Build/2015/3-725)

[Анализатор Roslyn реального мира](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , также можно выполнить как [звонка](http://channel9.msdn.com/events/Build/2015/3-725)

[Несколько примеров на github, сгруппированные по три вида анализаторы](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Введение и обзор несколько окон анализатора](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>См. также

- [Общие сведения о анализаторы Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Дополнительные документы на сайте github операционные системы](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Правила FxCop реализуется с помощью анализаторов Roslyn на github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)