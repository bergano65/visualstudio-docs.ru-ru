---
title: "Устранение неполадок анализа кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e552570eb48b9210b366ebbfe157fe656ab3fe0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-analysis-issues"></a>Устранение проблем, связанных с анализом кода
Этот раздел содержит сведения об устранении неполадок для перечисленных ниже проблем анализа кода Visual Studio.  
  
-   [Изменения в Visual Studio 2010 правило набора, не отражаются в предыдущих версиях Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Изменения в Visual Studio 2010 правило набора, не отражаются в предыдущих версиях Visual Studio  
 При создании набора правил в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] , содержащего дочерний набор правил, изменение дочерний набор правил не может применяться в выполнение анализа кода на компьютерах с использованием более ранней версии Visual Studio. Чтобы устранить эту проблему, необходимо принудительно перезаписать родительский набор правил, который является набор правил, содержащий дочерний набор правил.  
  
1.  Откройте родительский набор правил [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Внесите изменения, такие как добавление или удаление правила, а затем сохраните набор правил.  
  
3.  Повторно откройте набор правил, отменить изменение и сохраните снова набора правил.  
  
## <a name="see-also"></a>См. также  
 [Анализ качества приложения](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)