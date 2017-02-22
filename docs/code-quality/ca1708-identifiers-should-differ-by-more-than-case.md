---
title: "CA1708: идентификаторы должны отличаться не только регистром | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldDifferByMoreThanCase"
  - "CA1708"
helpviewer_keywords: 
  - "CA1708"
  - "IdentifiersShouldDifferByMoreThanCase"
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1708: идентификаторы должны отличаться не только регистром
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Имена двух типов, членов, параметров или полные имена двух пространств имен полностью совпадают при преобразовании знаков в нижний регистр.  
  
## Описание правила  
 Идентификаторы пространств имен, типов, членов и параметров не могут отличаться только регистром знаков, поскольку языки программирования, поддерживаемые средой CLR, не обязательно учитывают регистр знаков.  Например, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] является широко используемым языком, в котором не учитывается регистр.  
  
 Данное правило распространяется только на открытые члены.  
  
## Устранение нарушений  
 Выберите имя, которое является уникальным при сравнении с другими идентификаторами без учета регистра.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Библиотека может стать недоступной в некоторых языках среды [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Пример нарушения  
 В следующем примере демонстрируется нарушение данного правила.  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## Связанные правила  
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)