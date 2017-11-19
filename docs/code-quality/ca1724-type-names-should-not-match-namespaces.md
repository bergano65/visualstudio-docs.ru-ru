---
title: "CA1724: Имена типов не должны совпадать с пространствами имен | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 556fd9eee1bc453d4f9782459050367e18a3193b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724. Имена типов не должны совпадать с именами пространства имен
|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Имя типа соответствует [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] имена пространств имен при сравнении без учета регистра.  
  
## <a name="rule-description"></a>Описание правила  
 Имена типов не должны совпадать с именами пространств имен, определенными в библиотеке классов [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Нарушение этого правила приводит к уменьшению функциональности библиотеки.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Выберите имя типа, которое не соответствует имени [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] имен библиотеки классов.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 При разработке новых проектов нет известной выполняется сценарий, где необходимо подавить предупреждение из этого правила. Прежде чем можно подавить предупреждение, учитывайте, как пользователи библиотеки могут быть в замешательстве с соответствующим именем. При поставке библиотек может потребоваться отключить предупреждение из этого правила.