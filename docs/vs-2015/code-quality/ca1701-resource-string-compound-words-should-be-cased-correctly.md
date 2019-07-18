---
title: CA1701. Составных словах строк ресурса должны иметь правильный регистр | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 38d8195baa540c2c212c71938b6266e28df49101
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683065"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Категория|Microsoft.Naming|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Строка ресурса содержит составное слово, которое не иметь правильный регистр.

## <a name="rule-description"></a>Описание правила
 Каждое слово в строке ресурса разделяется на лексемы, с учетом регистра. Каждое непрерывное сочетание двух токенов проверяется библиотекой проверки орфографии Майкрософт. При совпадении слово создает нарушение правила. Примеры составных словах, вызывать нарушение: «Контрольная сумма» и «MultiPart», должны иметь правильный регистр как «Контрольная сумма» и «Multipart», соответственно. Из-за предыдущего общего использования несколько исключений, встроенные в правила, и помечаются несколько отдельные слова, такие как «Toolbar» и «Filename», который следует использовать правильный регистр определенных слов. В этом примере будет отмечена «ToolBar» и «FileName».

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Измените слово, чтобы регистр.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если обе части составного слова распознаются словарем и предполагается использовать два слова.

 Можно также добавить составных слов в пользовательский словарь для проверки орфографии. Слова в пользовательский словарь не вызывают нарушений. Дополнительные сведения см. в разделе [Практическое руководство. Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Связанные правила
 [CA1702: Составные слова должны иметь правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>См. также
 [Соглашения о написании прописными буквами](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d) [рекомендации по именованию](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)
