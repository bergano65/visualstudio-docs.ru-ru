---
title: Устранение проблем, связанных с анализом кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7cf8d516928f58976c77e9de13d8966ca3ca377a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031374"
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

- [Анализ качества приложения](../code-quality/code-analysis-for-managed-code-overview.md)
- [Анализ качества управляемого кода](../code-quality/code-analysis-for-managed-code-overview.md)
- [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)