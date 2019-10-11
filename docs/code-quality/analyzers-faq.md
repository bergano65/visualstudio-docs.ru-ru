---
title: EditorConfig и анализаторы
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aec8c26a827a39abdfeacfc0e3d6dea4a62db43
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999973"
---
# <a name="code-analysis-faq"></a>Анализ кода: вопросы и ответы

На этой странице содержатся ответы на некоторые часто задаваемые вопросы об анализе кода на основе .NET Compiler Platform в Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Анализ кода и EditorConfig

**ВОПРОС**. Следует ли использовать анализ кода или EditorConfig для проверки стиля кода?

**Ответ**. Анализ кода и файлы EditorConfig работают с руки. При определении стилей кода [в файле EditorConfig](../ide/editorconfig-code-style-settings-reference.md) или на странице [параметров текстового редактора](../ide/code-styles-and-code-cleanup.md) вы фактически настраиваете анализаторы кода, встроенные в Visual Studio. Файлы EditorConfig также можно использовать для настройки некоторых пакетов анализатора NuGet, таких как [FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig и наборы правил

**ВОПРОС**. Следует ли настроить мои анализаторы с помощью набора правил или файла EditorConfig?

**Ответ**. Наборы правил и файлы EditorConfig могут сосуществовать, и их можно использовать для настройки анализаторов. [Наборы правил](analyzer-rule-sets.md) позволяют включать и отключать правила и задавать их серьезность. Файлы EditorConfig предлагают другие способы настройки правил. Для средств FxCop Analyzer файлы EditorConfig позволяют [определить, какие типы кода следует проанализировать](fxcop-analyzer-options.md). Для анализаторов в стиле кода, встроенных в Visual Studio, файлы EditorConfig позволяют [определить предпочтительные стили кода](../ide/editorconfig-code-style-settings-reference.md) для базы кода.

Помимо наборов правил и файлов EditorConfig, некоторые анализаторы настраиваются с помощью текстовых файлов, помеченных как [Дополнительные файлы](../ide/build-actions.md#build-action-values) для компиляторов C# и VB.

> [!NOTE]
> EditorConfig файлы нельзя использовать для настройки анализа прежних версий, тогда как наборы правил могут.

## <a name="code-analysis-in-ci-builds"></a>Анализ кода в сборках CI

**ВОПРОС**. Работает ли анализ кода на основе .NET Compiler Platform в сборках непрерывной интеграции (CI)?

**Ответ**. Да. Для анализаторов, установленных из пакета NuGet, эти правила [применяются во время сборки, в](roslyn-analyzers-overview.md#build-errors)том числе во время сборки CI. Анализаторы, используемые в CI, строят конфигурацию правил из [наборов правил](analyzer-rule-sets.md) и [файлов editorconfig](configure-fxcop-analyzers.md). В настоящее время анализаторы кода, встроенные в Visual Studio, недоступны в качестве пакета NuGet, поэтому эти правила не могут быть применены в сборке CI.

## <a name="ide-analyzers-versus-stylecop"></a>Анализаторы IDE и StyleCop

**ВОПРОС**. В чем разница между анализаторами кода IDE Visual Studio и анализаторами StyleCop?

**Ответ**. Интегрированная среда разработки Visual Studio включает встроенные анализаторы, которые ищут как проблемы, связанные с стилем кода, так и качеством. Эти правила помогают использовать новые возможности языка по мере их появлении и улучшают удобство обслуживания кода. Анализаторы IDE постоянно обновляются в каждом выпуске Visual Studio.

[Анализаторы StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) — это сторонние анализаторы, установленные в виде пакета NuGet, который проверяет согласованность стилей в коде. Как правило, правила StyleCop позволяют задавать персональные настройки для базы кода без необходимости использовать один стиль в другом.

## <a name="code-analyzers-versus-legacy-analysis"></a>Анализаторы кода и анализ прежних версий

**ВОПРОС**. В чем разница между устаревшим анализом и анализом кода на основе .NET Compiler Platform?

Ответ **. анализ кода на основе**.NET Compiler Platform анализирует исходный код в режиме реального времени и во время компиляции, в то время как устаревший анализ анализирует двоичные файлы после завершения сборки. Дополнительные сведения см. в статье вопросы и ответы по [анализу на основе .NET Compiler Platform сравнению с устаревшим анализом](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) и [FxCop Analyzer](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Обрабатывать предупреждения как ошибки

**ВОПРОС**. В моем проекте используется параметр сборки для обработки предупреждений как ошибок. После перехода с предыдущего анализа на анализ исходного кода все предупреждения анализа кода будут отображаться как ошибки. Как предотвратить это?

**Ответ**. Чтобы предотвратить невозможность обработки предупреждений анализа кода как ошибок, выполните следующие действия.

  1. Создайте файл. props со следующим содержимым:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Добавьте строку в файл проекта. csproj или. vbproj, чтобы импортировать файл PROPS, созданный на предыдущем шаге. Эту строку необходимо поместить перед любыми строками, которые импортируют файлы FxCop Analyzer. props. Например, если файл. props имеет имя CODEANALYSIS. props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>См. также

- [Обзор анализаторов](roslyn-analyzers-overview.md)
- [Параметры соглашений о написании кода .NET в EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
