---
title: Наборы правил анализа кода в Visual Studio
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
ms.openlocfilehash: 20e727fd331ebd98a74acbb63738e6921e5ad1a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923059"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Задает использование правил для группировки правил анализа кода

При настройке анализа кода в Visual Studio можно выбрать из списка встроенных *наборов правил*. Набор правил относятся к проекту и группирование кода правила анализа, которые определяются целевые задачи и особые условия для этого проекта. Например можно применить набор правил, предназначенный для сканирования кода на наличие общедоступных API, или только минимальные правила и рекомендации. Также можно применять набор правил, который включает все правила.

Можно настроить набор правил путем добавления или удаления правил или изменяя степени серьезности правила отображаются в виде предупреждений и ошибок в **список ошибок**. Настраиваемые наборы правил могут соответствовать потребностям конкретной среды разработки. При настройке набора правил в редакторе набора правил предоставляет средства, помогающие в процессе поиска и фильтрации.

## <a name="rule-set-format"></a>Формат набора правил

Набор правил, указывается в формате XML в *.ruleset* файла. Правила, которые состоят из идентификатора и *действия*, группируются по Идентификатору анализатора и пространства имен в файле.

XML-содержимое *.ruleset* файла выглядит примерно так:

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
> Проще [изменить набор правил](../code-quality/working-in-the-code-analysis-rule-set-editor.md) в графическом **редактор набора правил** чем вручную.

Правило, задайте для проекта указан по `CodeAnalysisRuleSet` свойство в файле проекта Visual Studio. Пример:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>См. также

- [Справочник по набору правил анализа кода](../code-quality/rule-set-reference.md)
