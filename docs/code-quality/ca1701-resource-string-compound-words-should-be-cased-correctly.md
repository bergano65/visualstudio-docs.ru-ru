---
title: CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed5ae8c0845755fe626e7e801f500389f9263cf5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234365"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Категория|Microsoft. Naming|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Строка ресурса содержит составное слово, которое по-видимому не имеет корректного регистра.

## <a name="rule-description"></a>Описание правила

Каждое слово в строке ресурса разбивается на маркеры, основанные на регистре. Каждое непрерывное сочетание двух токенов проверяется библиотекой проверки орфографии Майкрософт. При совпадении слово создает нарушение правила. Примерами составных слов, которые вызывают нарушение, являются "CheckSum" и "MultiPart", которые должны иметь регистр "checksum" и "multipart" соответственно. Из-за предыдущего распространенного использования в правило встроено несколько исключений, и несколько отдельных слов помечаются, например "Toolbar" и "filename", которые должны иметь регистр в два разных слова. В этом примере помечаются "ToolBar" и "FileName".

Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Измените слово так, чтобы оно было правильным.

## <a name="change-the-dictionary-language"></a>Изменение языка словаря

По умолчанию используется английская версия (EN) средства проверки орфографии. Если вы хотите изменить язык средства проверки орфографии, это можно сделать, добавив в файл *AssemblyInfo.CS* или *AssemblyInfo. vb* один из следующих атрибутов:

- Используйте <xref:System.Reflection.AssemblyCultureAttribute> , чтобы указать язык и региональные параметры, если ресурсы находятся во вспомогательной сборке.
- Используйте <xref:System.Resources.NeutralResourcesLanguageAttribute> , чтобы указать *нейтральную культуру* сборки, если ресурсы находятся в той же сборке, что и код.

> [!IMPORTANT]
> Если для языка и региональных параметров задано значение, отличное от английского языка и региональных параметров, это правило анализа кода автоматически отключается.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Предупреждение из этого правила можно отключить, если оба фрагмента составного слова распознаются словарем правописания, и цель состоит в использовании двух слов.

Можно также добавлять составные слова в пользовательский словарь для средства проверки орфографии. Слова в пользовательском словаре не вызывают нарушений. Дополнительные сведения см. в разделе [Практическое руководство. Настройка словаря](../code-quality/how-to-customize-the-code-analysis-dictionary.md)анализа кода.

## <a name="related-rules"></a>Связанные правила

- [CA1702 Составные слова должны иметь правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709 Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Идентификаторы должны отличаться более чем регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>См. также

- [Соглашения о написании прописными буквами](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Правила именования](/dotnet/standard/design-guidelines/naming-guidelines)