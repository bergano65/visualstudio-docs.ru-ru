---
title: Отображение поддерживаемых пакетов Рослин
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd268dadd03ee5d648075ccea1763e949719c90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701321"
---
# <a name="net-compiler-platform-package-version-reference"></a>Ссылка на пакет пакетов платформы компилятора .NET

В следующей таблице показано, какие версии [пакетов платформы компилятора .NET (Roslyn)](https://www.nuget.org/packages/Microsoft.Net.Compilers/) поддерживаются для различных версий Visual Studio.

Например, чтобы гарантировать, что пользовательский анализатор работает на всех версиях Visual Studio 2017, он должен быть нацелен на версию 2.0 Microsoft.Net.Compilers.

| Версия пакета Roslyn | Минимальная поддержка визуальной версии studio |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 версии 15.9 |
| 2.9.0 | Visual Studio 2017 версии 15.8 |
| 2.8.2 | Visual Studio 2017 версии 15.7 |
| 2.7.0 | Visual Studio 2017 версии 15.6 |
| 2.6.1 | Visual Studio 2017 версии 15.5 |
| 2.4.0 | Visual Studio 2017 версии 15.4 |
| 2.3.2 | Visual Studio 2017 версия 15.3 |
| 2.2.0 | Visual Studio 2017 версии 15.2 |
| 2.1.0 | Visual Studio 2017 версии 15.1 |
| 2.0.0 | Визуальная студия 2017 RTM |
| 1.3.2 | Визуальное обновление студии 2015 3 |
| 1.2.2 | Визуальное обновление студии 2015 |
| 1.1.1 | Визуальное обновление студии 2015 1 |
| 1.0.1 | Визуальная студия 2015 RTM |

> [!TIP]
> Для пакетов Roslyn, где минимально поддерживаемая версия Visual Studio является версия Visual Studio 2017, все версии Visual Studio 2019 также поддерживаются, потому что они пришли позже.

## <a name="see-also"></a>См. также

- [Пакет SDK для .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
- [Начало работы с анализаторов Roslyn](getting-started-with-roslyn-analyzers.md)
