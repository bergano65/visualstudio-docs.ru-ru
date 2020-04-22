---
title: EditorConfig против анализаторов
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56b0c0defe5593c9dc0e2111ef5984a5c51eaf55
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760131"
---
# <a name="code-analysis-faq"></a>Анализ кода часто задаваемые вопросы

Эта страница содержит ответы на некоторые часто задаваемые вопросы об анализе кода платформы на основе .NET Compiler в Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Анализ кода против EditorConfig

**В:** Должен ли я использовать анализ кода или EditorConfig для проверки стиля кода?

**A**: Анализ кода и файлы EditorConfig работают рука об руку. Когда вы определяете стили кода [в файле EditorConfig](../ide/editorconfig-code-style-settings-reference.md) или на странице [опций текстового редактора,](../ide/code-styles-and-code-cleanup.md) вы настраиваете анализаторы кода, встроенные в Visual Studio. Файлы EditorConfig могут использоваться для включения или отсрочки правил анализатора, а также для настройки некоторых пакетов анализаторов NuGet, таких как [анализаторы FxCop.](configure-fxcop-analyzers.md)

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig против наборов правил

**В:** Должен ли я настроить анализаторы с помощью набора правил или файла EditorConfig?

**A**: Наборы правил и файлы EditorConfig могут сосуществовать и могут использоваться для настройки анализаторов. Файлы И наборы правил EditorConfig позволяют включить и отключить правила и установить их серьезность.

Тем не менее, файлы EditorConfig предлагают дополнительные способы настройки правил:

- Для анализаторов FxCop файлы EditorConfig позволяют [определить, какие типы кода анализировать.](fxcop-analyzer-options.md)
- Для анализаторов в стиле кода, встроенных в Visual Studio, файлы EditorConfig позволяют [определить предпочтительные стили кода](../ide/editorconfig-code-style-settings-reference.md) для базы кода.

В дополнение к наборам правил и файлам EditorConfig, некоторые анализаторы настраиваются с помощью текстовых файлов, отмеченных в качестве [дополнительных файлов](../ide/build-actions.md#build-action-values) для компиляторов C и VB.

> [!NOTE]
> - Файлы EditorConfig могут использоваться только для включения правил и установления их серьезности в версии Visual Studio 2019 16.3 и позже.
> - Файлы EditorConfig не могут быть использованы для настройки устаревшего анализа, в то время как наборы правил могут.

## <a name="code-analysis-in-ci-builds"></a>Анализ кода в сборках CI

**В:** Работает ли анализ кода на основе платформы .NET Compiler в непрерывных сборках интеграции (CI)?

**A:** Да. Для анализаторов, установленных из пакета NuGet, эти правила [применяются во время сборки,](roslyn-analyzers-overview.md#build-errors)в том числе во время сборки CI. Анализаторы, используемые в CI, создают конфигурацию правил соблюдения как из наборов правил, так и из файлов EditorConfig. В настоящее время анализаторы кода, встроенные в Visual Studio, не доступны в виде пакета NuGet, и поэтому эти правила не подлежат исполнению в сборке CI.

## <a name="ide-analyzers-versus-stylecop"></a>Анализаторы IDE против StyleCop

**В:** В чем разница между анализаторами кода Visual Studio IDE и анализаторами StyleCop?

**A**: Visual Studio IDE включает встроенные анализаторы, которые ищут как стиль кода, так и проблемы качества. Эти правила помогают использовать новые языковые функции по мере их внедрения и улучшают удобство обслуживания кода. Анализаторы IDE постоянно обновляются с каждым выпуском Visual Studio.

[Анализаторы StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) — это сторонние анализаторы, установленные в виде пакета NuGet, которые проверяют согласованность стиля в коде. Как правило, правила StyleCop позволяют устанавливать личные предпочтения для базы кода, не рекомендуя один стиль другому.

## <a name="code-analyzers-versus-legacy-analysis"></a>Анализаторы кода и анализ наследия

**В:** В чем разница между устаревшим анализом и анализом кода на основе платформы .NET Compiler?

**A**: анализ кода на основе платформы .NET Compiler анализирует исходный код в режиме реального времени и во время компиляции, в то время как устаревший анализ анализирует двоичные файлы после завершения сборки. Для получения дополнительной информации [FxCop analyzers FAQ](fxcop-analyzers-faq.md)см. [.NET Compiler Platform-based analysis versus legacy analysis](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis)

## <a name="treat-warnings-as-errors"></a>Рассматривать предупреждения как ошибки

**В:** Мой проект использует опцию сборки для обработки предупреждений как ошибок. После перехода от устаревшего анализа к анализу исходного кода все предупреждения об анализе кода теперь отображаются как ошибки. Как я могу предотвратить это?

**A:** Чтобы предотвратить обработку предупреждений об анализе кода как ошибки, выполните следующие действия:

  1. Создайте файл .props со следующим содержанием:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Добавьте строку в файл проекта .csproj или .vbproj для импорта файла .props, созданного на предыдущем этапе. Эта строка должна быть размещена перед любыми строками, которые импортируют файлы анализаля FxCop .props. Например, если ваш файл .props назван codeanalysis.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Страница решения для анализа кода

**В:** Где находится страница свойства анализа кода для решения?

**A:** Страница свойства code Analysis на уровне решения была удалена в пользу более надежной группы общего имущества. Для управления анализом кода на уровне проекта по-прежнему доступна страница свойства code Analysis. (Для управляемых проектов мы также рекомендуем перейти из правил в EditorConfig для конфигурации правил.)  Для совместного использования правил в нескольких/всех проектах в рамках решения или репо мы рекомендуем определить группу свойств с свойством CodeAnalysisRuleSet в файле общего реквизита/целей или файле Directory.props/Directory.targets. Если у вас нет таких общих реквизитов или целей, которые импортируются все ваши проекты, следует рассмотреть вопрос о добавлении такой группы свойств в [каталог Directory.props или directory.targets в каталоге решений верхнего уровня, который автоматически импортируется во все файлы проекта, определенные в каталоге или его подкаталогах.](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build?directorybuildprops-and-directorybuildtargets)

## <a name="see-also"></a>См. также раздел

- [Обзор анализаторов](roslyn-analyzers-overview.md)
- [Параметры соглашений о написании кода .NET в EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
