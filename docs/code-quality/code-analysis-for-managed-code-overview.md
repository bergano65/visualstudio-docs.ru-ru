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
ms.openlocfilehash: e6515c0df7a9c3389e754d5238788d716be49e2e
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800090"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Общие сведения об анализе кода для управляемого кода в Visual Studio

Visual Studio может выполнять анализ кода управляемого кода двумя способами:
- С [прежним анализом](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), также известным как статический анализ для управляемых сборок FxCop.
- С помощью современных [анализаторов кода на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Анализаторы кода на основе .NET Compiler Platform, которые анализируют код в режиме реального времени по мере ввода, заменяют устаревший анализ статического кода FxCop, который анализирует только скомпилированный код.