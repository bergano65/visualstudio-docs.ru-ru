---
title: Устранение проблем, связанных с анализом кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1c80e7421569804f6d6781b117522dd1ef1dea8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885893"
---
# <a name="troubleshooting-code-analysis-issues"></a>Устранение проблем, связанных с анализом кода
В этом разделе приводятся сведения об устранении указанных ниже неполадок, связанных с анализом кода в Visual Studio.

-   [Изменения в наборе правил Visual Studio 2010 не отражаются в предыдущих версиях Visual Studio](#ChildRuleSetChangesInPreviousVersions)

##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Изменения в наборе правил Visual Studio 2010 не отражаются в предыдущих версиях Visual Studio
 При создании в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] набора правил, содержащего дочерний набор правил, изменения, внесенные в дочерний набор правил, могут не применяться при анализе кода на компьютерах, на которых используется предыдущая версия Visual Studio. Для устранения этой проблемы необходимо принудительно перезаписать родительский набор правил, то есть набор правил, содержащий дочерний набор.

1. Откройте родительский набор правил в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].

2. Внесите изменение, например добавьте или удалите правило, а затем сохраните набор правил.

3. Повторно откройте набор правил, отмените изменение, а затем сохраните набор правил повторно.

## <a name="see-also"></a>См. также
 [Анализ качества приложений](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md) [Анализ качества управляемого кода](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) [использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)