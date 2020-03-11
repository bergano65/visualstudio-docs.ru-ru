---
title: Сравнение EditorConfig и анализаторов
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408826"
---
# <a name="code-analysis-faq"></a>Анализ кода: вопросы и ответы

Эта страница содержит ответы на некоторые часто задаваемые вопросы об анализе кода на основе .NET Compiler Platform в Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Сравнение анализа кода и EditorConfig

**Вопрос**. Следует ли использовать анализ кода или EditorConfig для проверки стиля кода?

**Ответ**. Анализ кода и файлы EditorConfig тесно связаны друг с другом. При определении стилей кода [в файле EditorConfig](../ide/editorconfig-code-style-settings-reference.md) или на странице [параметров текстового редактора](../ide/code-styles-and-code-cleanup.md) вы фактически настраиваете анализаторы кода, встроенные в Visual Studio. Файлы EditorConfig можно использовать для включения или отключения правил анализатора, а также для настройки некоторых пакетов анализатора NuGet, таких как [анализаторы FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>Сравнение EditorConfig и наборов правил

**Вопрос**. Следует ли настраивать анализаторы с помощью набора правил или файла EditorConfig?

**Ответ**. Наборы правил и файлы EditorConfig могут сосуществовать, и их можно использовать для настройки анализаторов. Как файлы EditorConfig, так и наборы правил позволяют включать и отключать правила и задавать их важность.

Однако файлы EditorConfig предоставляют дополнительные способы настройки правил:

- Для анализаторов FxCop файлы EditorConfig позволяют [определить, какие типы кода следует анализировать](fxcop-analyzer-options.md).
- Для анализаторов стиля кода, встроенных в Visual Studio, файлы EditorConfig позволяют [определить предпочтительные стили кода](../ide/editorconfig-code-style-settings-reference.md) для базы кода.

Кроме наборов правил и файлов EditorConfig, некоторые анализаторы настраиваются с помощью текстовых файлов, помеченных в качестве [дополнительных файлов](../ide/build-actions.md#build-action-values) для компиляторов C# и VB.

> [!NOTE]
> - Файлы EditorConfig можно использовать только для включения правил и настройки их важности в Visual Studio 2019 версии 16.3 и более поздних.
> - Файлы EditorConfig не подходят для настройки анализа прежних версий, а наборы правил подходят.

## <a name="code-analysis-in-ci-builds"></a>Анализ кода в сборках CI

**Вопрос**. Работает ли анализ кода на основе .NET Compiler Platform в сборках непрерывной интеграции (CI)?

**Ответ**. Да. Для анализаторов, устанавливаемых из пакета NuGet, эти правила [принудительно применяются во время сборки](roslyn-analyzers-overview.md#build-errors), включая время сборки CI. Анализаторы, используемые в сборках CI, учитывают конфигурацию правил как из наборов правил, так и из файлов EditorConfig. Сейчас анализаторы кода, встроенные в Visual Studio, недоступны в качестве пакета NuGet, поэтому эти правила не могут быть применены в сборке CI.

## <a name="ide-analyzers-versus-stylecop"></a>Сравнение анализаторов IDE и StyleCop

**Вопрос**. В чем разница между анализаторами кода Visual Studio IDE и анализаторами StyleCop?

**Ответ**. Интегрированная среда разработки Visual Studio IDE включает встроенные анализаторы, которые определяют проблемы, связанные как со стилем кода, так и с качеством. Эти правила помогают использовать новые возможности языка по мере их появления и улучшают удобство обслуживания кода. Анализаторы IDE постоянно обновляются в каждом выпуске Visual Studio.

[Анализаторы StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) — это сторонние анализаторы, устанавливаемые в виде пакета NuGet, которые проверяют согласованность стиля в коде. В общем случае правила StyleCop позволяют задавать персональные настройки для базы кода без необходимости рекомендовать один стиль вместо другого.

## <a name="code-analyzers-versus-legacy-analysis"></a>Сравнение анализаторов кода и анализа прежних версий

**Вопрос**. В чем разница между анализом прежних версий и анализом кода на основе .NET Compiler Platform?

**Ответ**. Анализ кода на основе .NET Compiler Platform анализирует исходный код в режиме реального времени и во время компиляции, в то время как анализ прежних версий анализирует двоичные файлы после завершения сборки. Дополнительные сведения см. в разделах [Анализ на основе платформы .NET Compiler Platform и устаревшая функция анализа](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) и [Часто задаваемые вопросы по анализаторам FxCop](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Обработка предупреждений как ошибок

**Вопрос**. В моем проекте используется параметр сборки для обработки предупреждений как ошибок. После перехода с анализа прежних версий на анализ исходного кода все предупреждения анализа кода отображаются как ошибки. Как предотвратить это?

**Ответ**. Чтобы предотвратить обработку предупреждений анализа кода как ошибок, сделайте следующее:

  1. Создайте файл PROPS со следующим содержимым:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Добавьте в файл проекта CSPROJ или VBPROJ строку, чтобы импортировать файл PROPS, созданный на предыдущем шаге. Эту строку следует расположить до любых строк, которые импортируют файлы PROPS анализатора FxCop. Например, если файл PROPS имеет имя codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>См. также

- [Обзор анализаторов](roslyn-analyzers-overview.md)
- [Параметры соглашений о написании кода .NET в EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
