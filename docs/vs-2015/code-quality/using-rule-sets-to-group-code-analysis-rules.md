---
title: Использование наборов правил для группировки правил анализа кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603484"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Использование наборов правил для группировки правил анализа кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При настройке анализа кода в [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] или [!INCLUDE[vsPro](../includes/vspro-md.md)] можно выбрать из списка встроенных *наборов правил*Майкрософт. Набор правил — это логическая группа правил анализа кода, которая определяет целевые проблемы и конкретные условия. Например, можно применить набор правил, предназначенный для просмотра кода для общедоступных API-интерфейсов, или применить набор правил, включающий только минимальные Рекомендуемые правила. Можно также применить набор правил, включающий все правила.

 Набор правил можно настроить, добавляя или удаляя правила, либо изменяя правила, отображаемые в **Список ошибок** окне в виде предупреждений или ошибок. Настроенные наборы правил могут удовлетворить потребности конкретной среды разработки. При настройке набора правил на странице «набор правил» предоставляются средства поиска и фильтрации, помогающие в процессе.

## <a name="common-tasks"></a>Общие задачи

|Задача|Связанное содержимое|
|----------|---------------------|
|Практическое руководство **.** Используйте средства анализа кода, чтобы указать настраиваемый набор правил для поиска и исправления проблем в простом .NET Framework приложении.|-   [Пошаговое руководство. Настройка и использование настраиваемого набора правил](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Настройка анализа кода для проекта.** Выберите существующий набор правил для проекта, веб-сайта или решения.|-   [Как настроить анализ кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Использование наборов правил для указания выполняемых правил C++](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Как настроить анализ кода для веб-приложения ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Как указать наборы правил для нескольких проектов в решении](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Настройка набора правил.** Укажите правила, которые следует применить к проекту.|-   [Создание настраиваемых наборов правил](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Общие сведения о встроенных наборах правил.** Просмотр правил анализа кода, которые составляют встроенные наборы правил.|-   [Справочник по набору правил анализа кода](../code-quality/code-analysis-rule-set-reference.md)|
|**Интегрируйте анализ кода с Team Foundation Server:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] политики возврата, позволяющие группам разработчиков убедиться, что все возвраты кода соответствуют общему набору стандартов анализа кода.|-   [Как синхронизировать наборы правил проекта кода с политикой возврата командного проекта](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
