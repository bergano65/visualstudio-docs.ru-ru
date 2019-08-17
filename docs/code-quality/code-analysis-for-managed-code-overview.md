---
title: Анализ управляемого кода
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a44465b5f3daf89e915a5f6f5e7abe6c856598e5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546922"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Общие сведения об анализе кода для управляемого кода в Visual Studio

Visual Studio может выполнять анализ кода управляемого кода двумя способами: с [прежним анализом](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), также известным как статический анализ в виде FxCop для управляемых сборок, и с помощью современных [анализаторов кода](../code-quality/roslyn-analyzers-overview.md)на основе .NET Compiler Platform. Анализаторы кода на основе .NET Compiler Platform, которые анализируют код в режиме реального времени по мере ввода, заменяют устаревший анализ статического кода FxCop, который анализирует только скомпилированный код.

## <a name="see-also"></a>См. также

- [Обзор анализаторов на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
