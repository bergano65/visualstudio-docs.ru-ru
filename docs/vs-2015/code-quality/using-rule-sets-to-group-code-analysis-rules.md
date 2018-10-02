---
title: Использование наборов правил для группировки правил анализа кода | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ae7374ae6b713fe7fa1911cdcce3effa600482b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572230"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Использование наборов правил для группировки правил анализа кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [использование наборов правил для группировки правил анализа кода](https://docs.microsoft.com/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules).  
  
При настройке анализа кода в [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], или [!INCLUDE[vsPro](../includes/vspro-md.md)], можно выбрать из списка встроенных Microsoft *наборов правил*. Набор правил — это логическая группа правил анализа кода, которые определяют целевые задачи и определенные условия. Например можно применить набор правил, предназначенный для проверки кода для общедоступных API, или применить набора правил, который включает в себя минимально рекомендуемые правила. Можно также применить набора правил, который содержит все правила.  
  
 Вы можете настроить правило, в набор путем добавления или удаления правила, или изменить правила будет отображаться в **список ошибок** окно как предупреждения или ошибки. Настраиваемые наборы правил может соответствовать потребностям конкретной среды разработки. При настройке набора правил, страница набора правил предоставляет средства, помогающие в процессе поиска и фильтрации.  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Получите опыт практической:** использовать набор средств анализа кода, чтобы указать настраиваемое правило для поиска и устранения проблем в простом приложении .NET Framework.|-   [Пошаговое руководство: Настройка и использование набора настраиваемых правил](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**Настройка анализа кода для проекта:** выбрать существующее правило для проекта, веб-сайта или решения.|-   [Практическое: Настройка анализа кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Использование наборов правил для задания выполняемых правил C++](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Практическое: Настройка анализа кода для веб-приложения ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Практическое: определение набора правил для нескольких проектов в решении](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**Настройка набора правил:** задать правила для применения к проекту.|-   [Создание настраиваемых наборов правил](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**Понять наборов встроенных правил:** просмотра правил анализа кода, составляющие встроенных наборов правил.|-   [Справочник по набору правил анализа кода](../code-quality/code-analysis-rule-set-reference.md)|  
|**Интеграция анализа кода с Team Foundation Server:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] возврат политики позволяют командам разработки, чтобы убедиться в том, что все операции возврата кода удовлетворяют набору стандартов анализа кода.|-   [Практическое: синхронизация наборов правил проекта кода с политикой возврата командного проекта](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|



