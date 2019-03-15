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
ms.openlocfilehash: bec9296f15c48cf3b327c78cd0ce7d57adafa002
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57874684"
---
# <a name="analyzers-faq"></a>Анализаторы часто задаваемые вопросы

Эта страница содержит ответы на некоторые часто задаваемые вопросы о анализаторов Roslyn в Visual Studio.

## <a name="roslyn-analyzers-versus-editorconfig"></a>Анализаторы Roslyn и .editorconfig

**Q**: Использовать анализаторов Roslyn или .editorconfig для стиля кода?

**Ответ**. Анализаторы Roslyn и файлы editorconfig работать вручную идут рука об руку. При определении стили кода [в файле .editorconfig](../ide/editorconfig-code-style-settings-reference.md) или на [текстовый редактор параметров](../ide/code-styles-and-quick-actions.md) страницы, вы фактически настраиваете анализаторы Roslyn, которые встроены в Visual Studio. Файлы EditorConfig может также использоваться для настройки некоторых сторонних анализатора пакетов, таких как [анализаторы FxCop](configure-fxcop-analyzers.md).

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig и наборы правил

**Q**: Необходимо настроить Мои анализаторы, с помощью набора правил или файла с расширением editorconfig

**Ответ**. Наборы правил и файлов editorconfig являются взаимно исключают друг друга способа настройки анализаторы. Они могут сосуществовать. [Наборов правил](analyzer-rule-sets.md) позволяют включать и отключать правила и задавать их серьезности. Файлы EditorConfig имеют другие способы настройки правила. Анализаторы FxCop, файлы editorconfig позволяют [определить типы кода для анализа](fxcop-analyzer-options.md). Для анализаторов, которые встроены в Visual Studio, файлы editorconfig позволяют [определить стили предпочтительный кода](../ide/editorconfig-code-style-settings-reference.md) для базы кода.

Помимо наборов правил и файлы editorconfig, некоторые сторонние анализаторы настроены при помощи текстовых файлов с пометкой [дополнительные файлы](../ide/build-actions.md#build-action-values) для C# VB компиляторы и.

> [!NOTE]
> Файлы EditorConfig не может использоваться для настройки правила анализа статического кода, тогда как наборы правил.

## <a name="analyzers-in-ci-builds"></a>Анализаторы в построениях непрерывной Интеграции

**Q**: Работают ли анализаторы в построениях непрерывной интеграции (CI)?

**Ответ**. Да. Для анализаторов, которые установлены из пакета NuGet, эти правила заключены [применяются во время сборки](roslyn-analyzers-overview.md#build-errors), в том числе во время сборки CI. Анализаторы, используемый в конфигурации правил уважение сборок непрерывной Интеграции с обоих [наборов правил](analyzer-rule-sets.md) и [файлы editorconfig](configure-fxcop-analyzers.md). В настоящее время анализа кода, которые встроены в Visual Studio не предоставляется в виде пакета NuGet, и поэтому эти правила не могут быть осуществлены в сборки CI.

## <a name="ide-analyzers-versus-stylecop"></a>Анализаторы интегрированной среды разработки и StyleCop

**Q**: Какова разница между анализаторов кода интегрированной среды разработки Visual Studio и анализаторы StyleCop?

**Ответ**. Интегрированной среде разработки Visual Studio включает в себя встроенных средств, которые ищут обе проблемы стиля и качество кода. Эти правила помогают использовать новые возможности языка, так как они все представленные и повысить удобство поддержки кода. Интегрированная среда разработки анализаторов постоянно обновляются с каждым выпуском Visual Studio.

[Анализаторы StyleCop](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) такое анализаторы независимых производителей, установить в виде пакета NuGet, которые проверяют согласованность стиля в коде. В общем случае правил StyleCop позволяют задать базовый личные настройки для кода без рекомендацией один стиль на другой.

## <a name="analyzers-versus-static-code-analysis"></a>Анализаторы и статического анализа кода

**Q**: Какова разница между анализаторы и статического анализа кода?

**Ответ**. Анализаторы анализа исходного кода в режиме реального времени и во время компиляции, тогда как статический анализ кода анализирует двоичные файлы после завершения построения. Дополнительные сведения см. в разделе [анализаторов Roslyn и статического анализа кода](roslyn-analyzers-overview.md#roslyn-analyzers-vs-static-code-analysis) и [анализаторы FxCop часто задаваемые вопросы о](fxcop-analyzers-faq.md).

## <a name="see-also"></a>См. также

- [Обзор анализаторов](roslyn-analyzers-overview.md)
- [Параметры соглашений о написании кода .NET в EditorConfig](../ide/editorconfig-code-style-settings-reference.md)