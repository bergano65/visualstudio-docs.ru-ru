---
title: Миграция с FxCop Analyzer на анализаторы .NET
ms.custom: SEO-VS-2020
description: Сведения о переходе с средств FxCop Analyzer на анализаторы .NET
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112197"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Миграция с FxCop Analyzer на анализаторы .NET

Анализ исходного кода с помощью анализаторов .NET Compiler Platform ("Roslyn") заменяет [устаревший анализ](code-analysis-for-managed-code-overview.md) управляемому коду. Многие правила традиционного анализа (FxCop) уже были переписаны в качестве исходных анализаторов.

До Visual Studio 2019 16,8 и .NET 5,0 эти анализаторы поставляются как `Microsoft.CodeAnalysis.FxCopAnalyzers` [пакет NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

Начиная с Visual Studio 2019 16,8 и .NET 5,0, эти анализаторы [входят в состав пакета SDK для .NET](/dotnet/fundamentals/code-analysis/overview). Они также доступны в виде `Microsoft.CodeAnalysis.NetAnalyzers` [пакета NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). `Microsoft.CodeAnalysis.FxCopAnalyzers` Пакет NuGet скоро станет устаревшим.

## <a name="migration-steps"></a>Этапы миграции

Выполните следующие действия, чтобы перенести проект или решение из `Microsoft.CodeAnalysis.FxCopAnalyzers` в анализаторы .NET:

1. Удаление `Microsoft.CodeAnalysis.FxCopAnalyzers` пакета NuGet

2. [Включение или установка анализаторов .NET](install-net-analyzers.md)

3. Включить дополнительные правила: `Microsoft.CodeAnalysis.NetAnalyzers` гораздо более консервативн по сравнению с `Microsoft.CodeAnalysis.FxCopAnalyzers` . В отличие от пакета Фкскопанализерс, у него есть только несколько правил исправления, которые [по умолчанию включены как предупреждения сборки](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Можно [включить дополнительные правила](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) , настроив свойство MSBuild [аналисисмоде](/dotnet/core/project-sdk/msbuild-props#analysismode) . Например, если задать для свойства значение, `AllEnabledByDefault` по умолчанию будут включены все применимые правила центра сертификации в качестве предупреждений сборки.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>См. также раздел

- [Сравнение анализа исходного кода и устаревшей функции анализа](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Миграция из устаревшего анализа в анализаторы .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Включение или установка анализаторов .NET](install-net-analyzers.md)
- [Вопросы и ответы о анализаторах .NET](net-analyzers-faq.md)
- [Настройка анализаторов .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
