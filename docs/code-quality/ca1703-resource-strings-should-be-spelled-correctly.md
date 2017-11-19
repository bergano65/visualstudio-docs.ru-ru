---
title: "CA1703: Строки ресурсов должны иметь правильное правописание | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c7828aa218933208408a285510e998921d6f032
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: соблюдайте правильность написания строк ресурсов
|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Строка ресурса содержит одно или несколько слов, не распознанных библиотекой системы проверки правописания Майкрософт.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило анализирует строки ресурсов по словам, (маркирование составных слов) и проверку орфографии для всех слов и лексем. Сведения об алгоритме анализа см. в разделе [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 По умолчанию используется английский (en) версия средства проверки орфографии.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, используйте полные слова, которые написаны правильно, или добавьте слова в пользовательский словарь. Сведения об использовании пользовательских словарей см. в разделе [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Правильно написанные слова сокращают время, необходимое для получения новых библиотек программного обеспечения.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)