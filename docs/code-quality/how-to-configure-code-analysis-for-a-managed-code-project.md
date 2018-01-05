---
title: "Как: Настройка анализа кода для проекта управляемого кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 134645ced3352d820165b23a73308894fed0897a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Практическое руководство. Настройка анализа кода для проекта управляемого кода
В [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] и [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], можно выбрать из списка анализа кода *наборов правил* для применения к проекту управляемого кода. Набор правил по умолчанию — минимальные правила Microsoft для рекомендуется. Можно применить другой набор для проекта или для всех проектов в решении правил.  
  
> [!NOTE]
>  Сведения о настройке набора правил для веб-приложений ASP.NET см. в разделе [как: Настройка анализа кода для веб-приложения ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Чтобы настроить набор правил для проекта .NET Framework  
  
1.  В **обозревателе решений**, щелкните проект.  
  
2.  На **анализ** меню, нажмите кнопку **Настройка анализа кода для** *ProjectName*.  
  
3.  В **конфигурации** и **платформы** списки, выберите конфигурацию построения и целевую платформу.  
  
4.  Чтобы запустить анализ кода при каждом построении проекта с использованием выбранной конфигурации, выберите **включить анализ кода в построении (определяет константу CODE_ANALYSIS)** флажок. Можно также выполнить анализ кода вручную, открыв **анализ** меню и выбрав пункт **выполнить анализ кода в** *ProjectName*.  
  
5.  По умолчанию функция анализа кода выдает предупреждения, связанные с кодом, автоматически созданным внешними средствами. Чтобы просмотреть предупреждения из созданного кода, снимите **исключить результаты из созданного кода** флажок.  
  
    > [!NOTE]
    >  Этот параметр не отключает ошибки и предупреждения из созданного кода, если ошибки и предупреждения появляются в формах и шаблонах. Вы можете просматривать и обслуживать исходный код для формы или шаблона.  
  
6.  В **выполнить этот набор правил** выполните одно из следующих действий:  
  
    -   Выберите набор правил, который вы хотите использовать.  
  
    -   Нажмите кнопку  **\<Обзор... >** , чтобы указать существующий настраиваемый набор правил, нет в списке.  
  
    -   Определите настраиваемый набор правил.  
  
         Дополнительные сведения см. в разделе [Создание настраиваемых наборов правил](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Настройка и использование набора настраиваемых правил](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)