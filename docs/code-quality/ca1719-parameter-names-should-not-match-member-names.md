---
title: "CA1719: имена параметров не должны совпадать с именами элементов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldNotMatchMemberNames"
  - "CA1719"
helpviewer_keywords: 
  - "CA1719"
  - "ParameterNamesShouldNotMatchMemberNames"
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1719: имена параметров не должны совпадать с именами элементов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 При сравнении без учета регистра имя доступного для внешнего кода члена совпадает с именем одного из его параметров.  
  
## Описание правила  
 Имя параметра должно передавать смысловое значение параметра, а имя члена — смысловое значение члена.  Они могут совпадать лишь в очень редких случаях.  Присвоение параметру имени содержащего его члена кажется неестественным и затрудняет использование библиотеки.  
  
## Устранение нарушений  
 Выберите имя параметра, которое не совпадает с именем члена.  
  
## Отключение предупреждений  
 При разработке нового кода случаи, когда необходимо отключать предупреждения о нарушении данного правила, неизвестны.  В случае поставки библиотек подобные предупреждения, возможно, необходимо отключать.  
  
## Связанные правила  
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)