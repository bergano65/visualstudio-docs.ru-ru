---
title: "CA1708: Идентификаторы должны отличаться только регистром | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cda7936a1a701b1b51957a7038db496f70ddd9c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: идентификаторы должны отличаться не только регистром
|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Имена двух типов, членов, параметров и полное имя пространства имен идентичны, если они преобразуются в нижний регистр.  
  
## <a name="rule-description"></a>Описание правила  
 Идентификаторы пространств имен, типов, членов и параметров не могут отличаться только регистром знаков, поскольку языки программирования, поддерживаемые средой CLR, не обязательно учитывают регистр знаков. Например [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] — это широко используемый язык, без учета регистра.  
  
 Это правило срабатывает для только открытые члены.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Выберите имя, которое является уникальным при сравнении с другими идентификаторами регистра.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Библиотеки могут быть неприменимы в некоторых языках [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## <a name="example-of-a-violation"></a>Пример нарушения  
 В следующем примере показано нарушение этого правила.  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)