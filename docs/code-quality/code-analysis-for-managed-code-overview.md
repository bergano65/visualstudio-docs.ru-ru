---
title: Анализ управляемого кода
ms.date: 08/27/2020
description: Сведения об анализаторах кода на основе .NET Compiler Platform в Visual Studio. Узнайте, почему эти анализаторы заменяют статический анализ FxCop для управляемых сборок.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 643e8457dbbe838d593a7bad38064537b6cbe57d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348532"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Обзор анализа кода для .NET в Visual Studio

Visual Studio может выполнять анализ кода управляемого кода двумя способами: с [прежним анализом](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), также известным как статический анализ в виде FxCop для управляемых сборок, и с помощью современных [анализаторов кода на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Анализаторы кода на основе .NET Compiler Platform, которые анализируют код в режиме реального времени по мере ввода, заменяют устаревший анализ статического кода FxCop, который анализирует только скомпилированный код.
