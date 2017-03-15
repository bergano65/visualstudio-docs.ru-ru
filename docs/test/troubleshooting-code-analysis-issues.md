---
title: "Устранение проблем, связанных с анализом кода | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 5
---
# Устранение проблем, связанных с анализом кода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе содержатся сведения об устранении следующих проблем, связанных с анализом кода Visual Studio.  
  
-   [Изменения, внесенные в набор правил в Visual Studio 2010, не отображаются в предыдущих версиях Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Изменения, внесенные в набор правил в Visual Studio 2010, не отображаются в предыдущих версиях Visual Studio  
 При создании в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] набора правил, содержащего дочерний набор правил, изменения, внесенные в дочерний набор правил, могут не применяться в сеансах анализа кода, выполняемых на компьютерах с предыдущей версией Visual Studio.  Для устранения этой проблемы можно принудительно перезаписать родительский набор правил, то есть набор правил, содержащий дочерний набор правил.  
  
1.  Откройте родительский набор правил в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Внесите изменения, например добавьте или удалите правило, а затем сохраните набор правил.  
  
3.  Откройте повторно набор правил, отмените изменения, а затем сохраните его повторно.  
  
## См. также  
 [Анализ качества приложения](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)