---
title: 'CA1702: в составных словах следует указывать правильный регистр | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 76ce346430a249b562f00e17c3173e79128d1708
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669256"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: для сложных слов следует использовать правильный регистр
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю документацию по Visual Studio см. в разделе [CA1702: составные слова должны иметь правильный регистр](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly).

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое — при срабатывании сборок.<br /><br /> Не критическое — при срабатывании параметров типа.|

## <a name="cause"></a>Причина
 Имя идентификатора содержит несколько слов, а по крайней мере одно из слов является составным словом, которое не имеет правильного регистра.

## <a name="rule-description"></a>Описание правила
 Имя идентификатора разбивается на слова, основанные на регистре. Каждое смежное сочетание из двух слов проверяется библиотекой проверки орфографии (Майкрософт). Если оно распознано, идентификатор создает нарушение правила. Примерами составных слов, которые вызывают нарушение, являются "CheckSum" и "MultiPart", которые должны иметь регистр "checksum" и "multipart" соответственно. Из-за предыдущего распространенного использования в правило встроено несколько исключений, и несколько отдельных слов помечаются, например "Toolbar" и "filename", которые должны иметь регистр в двух различных словах (в данном случае это "ToolBar" и "FileName").

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Измените имя так, чтобы оно выполнялось правильно.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если оба фрагмента составного слова распознаются словарем правописания, и цель состоит в использовании двух слов.

## <a name="related-rules"></a>Связанные правила
 [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>См. также раздел
 [Рекомендации по именованию](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) [соглашения о прописных буквах](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
