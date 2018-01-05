---
title: "CA1719: Имена параметров не должны совпадать с именами элементов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1fd1d1af9287b73d9d1f44143e6673d2a67b690c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: имена параметров не должны совпадать с именами элементов
|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Имя видимого снаружи элемента соответствует при сравнении без учета регистра, имя одного из своих параметров.  
  
## <a name="rule-description"></a>Описание правила  
 Имя параметра должно передавать смысловое значение параметра, а имя члена — смысловое значение члена. Они могут совпадать лишь в очень редких случаях. Присвоение параметру имени содержащего его члена кажется неестественным и затрудняет использование библиотеки.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Выберите имя параметра, которое не соответствует имени элемента.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 При разработке новых проектов нет известной выполняется сценарий, где необходимо подавить предупреждение из этого правила. При поставке библиотек может потребоваться отключить предупреждение из этого правила.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)