---
title: Устранение проблем, связанных с анализом кода | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: b8d17fcaec0034d2803f769cc5595416f5d56de8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560384"
---
# <a name="troubleshooting-code-analysis-issues"></a>Устранение проблем, связанных с анализом кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Устранение проблем анализа кода](https://docs.microsoft.com/visualstudio/code-quality/troubleshooting-code-analysis-issues).  
  
В этом разделе приводятся сведения об устранении указанных ниже неполадок, связанных с анализом кода в Visual Studio.  
  
-   [Изменения в наборе правил Visual Studio 2010 не отражаются в предыдущих версиях Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Изменения в наборе правил Visual Studio 2010 не отражаются в предыдущих версиях Visual Studio  
 При создании в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] набора правил, содержащего дочерний набор правил, изменения, внесенные в дочерний набор правил, могут не применяться при анализе кода на компьютерах, на которых используется предыдущая версия Visual Studio. Для устранения этой проблемы необходимо принудительно перезаписать родительский набор правил, то есть набор правил, содержащий дочерний набор.  
  
1.  Откройте родительский набор правил в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
2.  Внесите изменение, например добавьте или удалите правило, а затем сохраните набор правил.  
  
3.  Повторно откройте набор правил, отмените изменение, а затем сохраните набор правил повторно.  
  
## <a name="see-also"></a>См. также  
 [Анализ качества приложения](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)



