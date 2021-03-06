---
title: Практическое руководство. Задание свойств анализа кода для проектов C / C++ | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 4ebed266924861dac4bfc9e316a56907dbd11534
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201317"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Практическое руководство. Установка свойств анализа кода для проектов C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно настроить средство анализа кода правил для анализа кода для каждой конфигурации проекта. Кроме того можно направить анализ кода, чтобы отключить предупреждения из кода, который был создан и добавлен в проект с помощью стороннего средства.  
  
## <a name="code-analysis-property-page"></a>Страница свойств анализа кода  
 **Анализа кода** страница свойств содержит все параметры конфигурации анализа кода для проекта. Чтобы открыть страницу свойств анализа кода для проекта в **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства**. Далее, нужно развернуть **свойства конфигурации** и выберите **анализа кода** вкладки.  
  
## <a name="project-configuration-and-platform"></a>Конфигурация и платформа проекта  
 **Конфигурации** списка и **платформы** позволяют применить разные параметры анализа кода к другому проекту сочетания конфигурации и платформы. Например можно направить анализа кода применение одного набора правил для проекта для отладочной сборки и создает другой набор для выпуска.  
  
## <a name="enabling-code-analysis"></a>Включение анализа кода  
 Вы можете включить анализ кода для проекта, выбрав **включить анализ кода для C/C++ при сборке**. В сочетании с **конфигурации** списка, например, можно отключить анализ кода для отладочных построений и включить его для построения выпуска.  
  
 Если проект содержит управляемый код, можно решить, следует ли включить или отключить анализ кода, выбрав **включить анализ кода в построении**.  
  
 Анализ кода призвана помочь вам повысить качество кода и избежать распространенных ошибок. Таким образом, необходимо рассмотреть необходимость отключения анализа кода. Как правило, лучше отключить наборов правил или отдельные правила, которые вы не хотите применить к проекту.  
  
## <a name="generated-code"></a>Созданный код  
 Разработчики часто используют средства для быстрой разработки приложений. Эти средства также создают код, который добавляется в проект. Может потребоваться нарушения правил, обнаруживаемых при анализе в созданном коде см. в разделе. Тем не менее может не потребоваться видны, если вы не хотите поддерживать код.  
  
 **Подавлять результаты из созданного кода** флажок на **Общие** страница свойств можно указать, хотите ли вы предупреждения при анализе кода из управляемого кода, который создается с помощью сторонних средств см. в разделе .  
  
## <a name="rule-sets"></a>Наборы правил  
 Если проект содержит управляемый код, можно выбрать правила, применяемые при анализе кода, выбрав набор правил в **выполнить этот набор правил** списка.  
  
## <a name="see-also"></a>См. также  
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Анализ кода для предупреждений C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
