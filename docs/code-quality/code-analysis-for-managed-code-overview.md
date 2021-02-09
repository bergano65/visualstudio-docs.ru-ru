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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 542747f650888b384a9f9c4910b0d9caea93e948
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860572"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Обзор анализа кода для .NET в Visual Studio

Visual Studio может выполнять анализ кода управляемого кода двумя способами: с [прежним анализом](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), также известным как статический анализ в виде FxCop для управляемых сборок, и с помощью современных [анализаторов кода на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Анализаторы кода на основе .NET Compiler Platform, которые анализируют код в режиме реального времени по мере ввода, заменяют устаревший анализ статического кода FxCop, который анализирует только скомпилированный код.
