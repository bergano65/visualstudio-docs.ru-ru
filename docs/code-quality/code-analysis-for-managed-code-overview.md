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
ms.openlocfilehash: f4e5aad0ffcd6febce411d952b1b36a0669b109a
ms.sourcegitcommit: bb72ce6ec173f3ae06c7ae57322c43690f27553c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2020
ms.locfileid: "76967310"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Общие сведения об анализе кода для управляемого кода в Visual Studio

Visual Studio может выполнять анализ кода управляемого кода двумя способами: с [прежним анализом](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), также известным как статический анализ в виде FxCop для управляемых сборок, и с помощью современных [анализаторов кода на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Анализаторы кода на основе .NET Compiler Platform, которые анализируют код в режиме реального времени по мере ввода, заменяют устаревший анализ статического кода FxCop, который анализирует только скомпилированный код.

