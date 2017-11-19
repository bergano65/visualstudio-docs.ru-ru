---
title: "CA1702: Сложных слов следует использовать правильный регистр | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c8606656b7ffe5f64c4c162b85d24bdbd9b1de0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: для сложных слов следует использовать правильный регистр
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое — при возникновении в сборках.<br /><br /> Не критическое — при возникновении в параметрах типов.|  
  
## <a name="cause"></a>Причина  
 Имя идентификатора состоит из нескольких слов и по крайней мере одно из указанных слов кажется является составным словом в неправильном регистре.  
  
## <a name="rule-description"></a>Описание правила  
 Имя идентификатора разбивается на слова с учетом регистра. Каждое непрерывное сочетание двух слов проверяется библиотекой проверки орфографии Майкрософт. Если он был распознан, идентификатор создает нарушение правила. Примерами составных слов, которые нарушают являются «Контрольная сумма» и «MultiPart», должны иметь правильный регистр как «Контрольная сумма» и «Multipart», соответственно. Из-за предыдущего общего использования нескольких исключений встроены в правило и помечены несколько отдельные слова, такие как «Панель инструментов» и «Имя файла», должны иметь правильный регистр определенных слов (в данном случае «Панель инструментов» и «FileName»).  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает обучения, необходимое для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Измените имя, чтобы регистр.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если обе части составного слова распознаются словарем и предполагается использование двух слов.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>См. также  
 [Правила именования](/dotnet/standard/design-guidelines/naming-guidelines)   
 [Соглашения о регистре](/dotnet/standard/design-guidelines/capitalization-conventions)