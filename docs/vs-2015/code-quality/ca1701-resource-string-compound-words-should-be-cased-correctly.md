---
title: 'CA1701: для составных слов в строках ресурсов следует указывать правильный регистр | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7610852f6d9fbea2fbd2dd10d478ad2d1a0da899
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669271"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: соблюдайте правильность регистра в составных словах строк ресурса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Категория|Microsoft. Naming|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Строка ресурса содержит составное слово, которое по-видимому не имеет корректного регистра.

## <a name="rule-description"></a>Описание правила
 Каждое слово в строке ресурса разбивается на маркеры, основанные на регистре. Каждое непрерывное сочетание двух токенов проверяется библиотекой проверки орфографии Майкрософт. При совпадении слово создает нарушение правила. Примерами составных слов, которые вызывают нарушение, являются "CheckSum" и "MultiPart", которые должны иметь регистр "checksum" и "multipart" соответственно. Из-за предыдущего распространенного использования в правило встроено несколько исключений, и несколько отдельных слов помечаются, например "Toolbar" и "filename", которые должны иметь регистр в два разных слова. В этом примере помечаются "ToolBar" и "FileName".

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Измените слово так, чтобы оно было правильным.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если оба фрагмента составного слова распознаются словарем правописания, и цель состоит в использовании двух слов.

 Можно также добавлять составные слова в пользовательский словарь для средства проверки орфографии. Слова в пользовательском словаре не вызывают нарушений. Дополнительные сведения см. в разделе [инструкции. Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Связанные правила
 [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>См. также раздел
 [Правила именования](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) [соглашений о капитализации](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
