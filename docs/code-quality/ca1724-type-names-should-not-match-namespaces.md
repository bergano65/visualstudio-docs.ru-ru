---
title: 'CA1724: Имена типов не должны совпадать с пространствами имен | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39e6b539d0259f83475e3e3a685bed7ffe6a7c87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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