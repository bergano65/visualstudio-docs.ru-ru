---
title: Наборы правил анализа кода
ms.date: 04/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ced442c0fafc47b5cdae1568dbbfb6df7c2f2f50
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948398"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Использование наборов правил для группировки правил анализа кода

При настройке анализа кода в Visual Studio, можно выбрать из списка встроенных *наборов правил*. Набор правил, применяется к проекту и — это группирование кода правила анализа, которые определяют целевые задачи и особые условия для этого проекта. Например можно применить набора правил, который предназначен для проверки кода для общедоступных API, или просто минимальный рекомендуемый правила. Можно также применить набора правил, который содержит все правила.

Вы можете настроить набор правил, добавление или удаление правил, или изменив степени серьезности правила отображаются в виде предупреждений или ошибок в **список ошибок**. Настраиваемые наборы правил может соответствовать потребностям конкретной среды разработки. При настройке набора правил, в редакторе набора правил предоставляет средства, помогающие в процессе поиска и фильтрации.

Доступные наборы правил для [статического анализа управляемого кода](how-to-configure-code-analysis-for-a-managed-code-project.md), [анализ кода C++](using-rule-sets-to-specify-the-cpp-rules-to-run.md), и [анализаторов Roslyn](analyzer-rule-sets.md).

## <a name="rule-set-format"></a>Формат набора правил

Набор правил, указывается в формате XML в *.ruleset* файла. Правила, которые состоят из идентификатора и *действие*, группируются по Идентификатору анализатора и пространства имен в файле.

Содержание *.ruleset* файла будет выглядеть этот XML-код:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Это упрощает [изменить набор правил](../code-quality/working-in-the-code-analysis-rule-set-editor.md) в графическом **редактор набора правил** чем вручную.

## <a name="specify-a-rule-set-for-a-project"></a>Укажите набор правил для проекта

Задайте для проекта задается правило **CodeAnalysisRuleSet** свойство в файле проекта Visual Studio. Пример:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>См. также

- [Справочник по набору правил анализа кода](../code-quality/rule-set-reference.md)