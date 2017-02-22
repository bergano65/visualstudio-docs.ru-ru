---
title: "CA1703: соблюдайте правильность написания строк ресурсов | Microsoft Docs"
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
  - "ResourceStringsShouldBeSpelledCorrectly"
  - "CA1703"
helpviewer_keywords: 
  - "CA1703"
  - "ResourceStringsShouldBeSpelledCorrectly"
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1703: соблюдайте правильность написания строк ресурсов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Строка ресурса содержит одно или несколько слов, не распознанных библиотекой системы проверки правописания Майкрософт.  
  
## Описание правила  
 Это правило анализирует строки ресурсов по словам \(составные слова разделяются на лексемы\) и проверяет правописание каждого слова и лексемы.  Сведения об алгоритме анализа см. в разделе [CA1704: идентификаторы должны иметь правильное написание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 По умолчанию используется англоязычная \("en"\) версия средства проверки орфографии.  
  
## Устранение нарушений  
 Чтобы исправить нарушение этого правила, используйте правильно написанные полные слова или добавьте слова в пользовательский словарь.  Сведения об использовании пользовательских словарей см. в разделе [CA1704: идентификаторы должны иметь правильное написание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  Соблюдение правописания позволяет быстрее изучать новые программные библиотеки.  
  
## Связанные правила  
 [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1704: идентификаторы должны иметь правильное написание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)