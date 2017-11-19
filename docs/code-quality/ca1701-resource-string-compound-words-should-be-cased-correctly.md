---
title: "CA1701: Составных словах строк ресурса следует использовать правильный регистр | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4dee5b21724944ea26e89c2cd1ace556f1377848
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: соблюдайте правильность регистра в составных словах строк ресурса
|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Строка ресурса содержит составное слово, которое не отображается в неправильном регистре.  
  
## <a name="rule-description"></a>Описание правила  
 Каждое слово в строке ресурса разделяется на лексемы, с учетом регистра. Каждое непрерывное сочетание двух токенов проверяется библиотекой проверки орфографии Майкрософт. При совпадении слово создает нарушение правила. Примерами составных слов, которые нарушают являются «Контрольная сумма» и «MultiPart», должны иметь правильный регистр как «Контрольная сумма» и «Multipart», соответственно. Из-за предыдущего общего использования несколько исключений, встроенные в правила, и обозначаются как несколько отдельных слов, например «Панель инструментов» и «Имя_файла», который должны иметь правильный регистр определенных слов. В этом примере будет отмечен «Панель инструментов» и «FileName».  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает обучения, необходимое для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Измените слово, чтобы регистр.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если обе части составного слова распознаются словарем и предполагается использование двух слов.  
  
 Можно также добавить составные слова в пользовательский словарь для проверки орфографии. Слова в пользовательский словарь не вызывают нарушений. Дополнительные сведения см. в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>См. также  
 [Соглашения о регистре](/dotnet/standard/design-guidelines/capitalization-conventions)   
 [Правила именования](/dotnet/standard/design-guidelines/naming-guidelines)