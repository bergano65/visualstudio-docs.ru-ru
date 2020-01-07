---
title: Анализ управляемого кода
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f32cf357cadafd6d5dd8166c23de15a16a8e502c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587763"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Общие сведения об анализе кода для управляемого кода в Visual Studio

Visual Studio может выполнять анализ кода управляемого кода двумя способами: с [прежним анализом](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), также известным как статический анализ в виде FxCop для управляемых сборок, и с помощью современных [анализаторов кода](../code-quality/roslyn-analyzers-overview.md)на основе .NET Compiler Platform. Анализаторы кода на основе .NET Compiler Platform, которые анализируют код в режиме реального времени по мере ввода, заменяют устаревший анализ статического кода FxCop, который анализирует только скомпилированный код.

## <a name="see-also"></a>См. также:

- [Обзор анализаторов на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
