---
title: "Использование наборов правил для группировки правил анализа кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 265ca57904cb47c52ecaf6ba260e726da9b8a063
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2018
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Использование наборов правил для группировки правил анализа кода

При настройке анализа кода в Visual Studio можно выбрать из списка встроенных Microsoft *наборов правил*. Набор правил — это логическая группа правил анализа кода, которые определяют целевые задачи и определенных условий. Например можно применить набор правил, предназначенный для сканирования кода на наличие общедоступных API, или можно применить набор, включающий только минимальный рекомендуемый набор правил. Также можно применять набор правил, который включает все правила.

Можно настроить правило, в набор путем добавления или удаления правил или изменить правила будет отображаться в **список ошибок** как предупреждения или ошибки. Настраиваемые наборы правил могут соответствовать потребностям конкретной среды разработки. При настройке набора правил, страница набора правил предоставляет средства, помогающие в процессе поиска и фильтрации.

## <a name="common-tasks"></a>Общие задачи

|Задача|Связанное содержимое|
|----------|---------------------|
|**Получите опыт практической работы:** использовать набор средств анализа кода, чтобы указать настраиваемое правило для поиска и устранения неполадок в простом приложении .NET Framework.|- [Пошаговое руководство: Настройка и использование набора настраиваемых правил](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Настройка анализа кода для проекта:** выбрать существующий набор правил для проекта, веб-сайта или решения.|- [Как: Настройка анализа кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />- [Использование наборов правил для задания выполняемых правил C++](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />- [Как: Настройка анализа кода для веб-приложения ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />- [Как: определение набора правил для нескольких проектов в решении](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Настройка набора правил:** задать правила для применения к проекту.|- [Создание настраиваемых наборов правил](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Понимать встроенных наборов правил:** просмотра правил анализа кода, входящие в состав встроенных наборов правил.|- [Справочник по набору правил анализа кода](../code-quality/code-analysis-rule-set-reference.md)|
|**Интеграция анализа кода с Team Foundation Server:** [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] возврат политики позволяют команде разработки, чтобы убедиться в том, что все возвраты кода удовлетворяют набору стандартов анализа кода.|- [Как: синхронизация наборов правил проекта кода с политикой возврата командного проекта](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|