---
title: Миграция с анализаторов FxCop на анализаторы .NET
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
ms.openlocfilehash: 5f9794c825012d682ca40dfdc5ebbfa03f0614ee
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398381"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Миграция с анализаторов FxCop на анализаторы .NET

Анализ исходного кода с помощью анализаторов .NET Compiler Platform ("Roslyn") заменяет [устаревший анализ](code-analysis-for-managed-code-overview.md) управляемому коду. Многие правила традиционного анализа (FxCop) уже были переписаны в качестве исходных анализаторов.

До Visual Studio 2019 16,8 и .NET 5,0 эти анализаторы поставляются как `Microsoft.CodeAnalysis.FxCopAnalyzers` [пакет NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

Начиная с Visual Studio 2019 16,8 и .NET 5,0, эти анализаторы [входят в состав пакета SDK для .NET](/dotnet/fundamentals/code-analysis/overview). Если вы не хотите переходить на пакет SDK для .NET 5 + или если предпочитаете использовать модель на основе пакетов NuGet, анализаторы также доступны в `Microsoft.CodeAnalysis.NetAnalyzers` [пакете NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Вы можете предпочесть модели на основе пакетов для обновления версий по требованию.

> [!NOTE]
> Сторонние анализаторы .NET не зависят от платформы. То есть проект не обязан ориентироваться на конкретную платформу .NET. Анализаторы работают для проектов, предназначенных для, а также для `net5.0` более ранних версий .NET, таких как `netcoreapp` , `netstandard` и `net472` .

## <a name="migration-steps"></a>Этапы миграции

Начиная с версии `3.3.2` , `Microsoft.CodeAnalysis.FxCopAnalyzers` пакет NuGet является устаревшим. Выполните следующие действия, чтобы перенести проект или решение из `Microsoft.CodeAnalysis.FxCopAnalyzers` в анализаторы .NET:

1. Удаление `Microsoft.CodeAnalysis.FxCopAnalyzers` пакета NuGet

2. [Включение или установка анализаторов .NET](install-net-analyzers.md). Обратите внимание, что не нужно изменять целевую платформу проекта.

3. Включить дополнительные правила: `Microsoft.CodeAnalysis.NetAnalyzers` гораздо более консервативн по сравнению с `Microsoft.CodeAnalysis.FxCopAnalyzers` . В отличие от пакета Фкскопанализерс, у него есть только несколько правил исправления, которые [по умолчанию включены как предупреждения сборки](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Можно [включить дополнительные правила](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) , настроив свойство MSBuild [аналисисмоде](/dotnet/core/project-sdk/msbuild-props#analysismode) . Например, если задать для свойства значение, `AllEnabledByDefault` по умолчанию будут включены все применимые правила центра сертификации в качестве предупреждений сборки.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>См. также раздел

- [Сравнение анализа исходного кода и устаревшей функции анализа](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Миграция с анализа прежних версий на анализаторы .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Включение или установка анализаторов .NET](install-net-analyzers.md)
- [Вопросы и ответы о анализаторах .NET](net-analyzers-faq.md)
- [Настройка анализаторов .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
