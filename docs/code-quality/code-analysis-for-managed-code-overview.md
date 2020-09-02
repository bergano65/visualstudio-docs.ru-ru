---
title: Анализ управляемого кода
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d13a8afdfcbeb6ae9f91e39779af8b82b2461000
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "89091409"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Обзор анализа кода для .NET в Visual Studio

Visual Studio может выполнять анализ кода управляемого кода двумя способами: с [прежним анализом](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), также известным как статический анализ в виде FxCop для управляемых сборок, и с помощью современных [анализаторов кода на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Анализаторы кода на основе .NET Compiler Platform, которые анализируют код в режиме реального времени по мере ввода, заменяют устаревший анализ статического кода FxCop, который анализирует только скомпилированный код.
