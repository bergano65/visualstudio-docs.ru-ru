---
title: Практическое руководство. Задание свойств анализа кода для проектов C/C++
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 1c517674bb3aba58caa865a02b384e9d90af8a10
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271698"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Практическое руководство. Задание свойств анализа кода для проектов C/C++

Можно указать, какие правила средство анализа кода использует для анализа кода в каждой конфигурации проекта. Кроме того, можно направлять анализ кода для подавления предупреждений из кода, созданного и добавленного в проект сторонним средством.

## <a name="code-analysis-property-page"></a>Страница свойств "анализ кода"

На странице свойств **анализ кода** содержатся все параметры конфигурации анализа кода для проекта MSBuild. Чтобы открыть страницу свойств анализ кода для проекта в **Обозреватель решений**, щелкните правой кнопкой мыши проект и выберите пункт **свойства**. Затем разверните узел **Свойства конфигурации** и выберите вкладку **анализ кода** .

## <a name="project-configuration-and-platform"></a>Конфигурация и платформа проекта

Список **конфигураций** и список **платформ** в верхней части окна позволяют применять различные параметры анализа кода к различным конфигурациям проекта и платформе. Например, можно направить анализ кода, чтобы применить один набор правил к проекту для отладочных сборок и другой набор для сборок выпуска.

## <a name="enabling-code-analysis"></a>Включение анализа кода

Вы можете включить анализ кода для проекта, включив параметр **Включить анализ кода Майкрософт** и включить параметры **Clang** , а также настроить его выполнение при сборке, выбрав **Включить анализ кода при сборке**. В сочетании с списком **конфигураций** можно, например, отключить анализ кода для отладочных сборок и включить его для сборок выпуска.

Анализ кода призван помочь вам повысить качество кода и избежать распространенных ловушек. Поэтому следует тщательно продумать необходимость отключения анализа кода. Обычно лучше отключить наборы правил, индивидуальные правила или отдельные проверки, которые не должны применяться к проекту.

## <a name="cmake-configuration"></a>Конфигурация CMak

В проектах CMak измените значение `enableMicrosoftCodeAnalysis` и `enableClangTidyCodeAnalysis` ключи в `CMakeSettings.json`, чтобы включить или отключить анализ кода. Дополнительные сведения см. [в разделе Использование Clang в Visual Studio](../code-quality/clang-tidy.md) .

## <a name="see-also"></a>См. также:

- [Анализ качества управляемого кода](../code-quality/code-analysis-for-managed-code-overview.md)
- [Анализ кода для предупреждений C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
- [Наборы правил для C++ кода](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Использование Clang](../code-quality/clang-tidy.md)
