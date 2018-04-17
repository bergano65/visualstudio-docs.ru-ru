---
title: 'CA1701: Составных словах строк ресурса следует использовать правильный регистр | Документы Microsoft'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d2579d50c6a82b4a2fdecaafbc43a904fd371ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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

## <a name="change-the-dictionary-language"></a>Изменить язык словаря

По умолчанию используется английский (en) версия средства проверки орфографии. Если вы хотите изменить язык проверки орфографии, это можно сделать, добавив один из следующих атрибутов к вашей *AssemblyInfo.cs* или *AssemblyInfo.vb* файла:

- Используйте <xref:System.Reflection.AssemblyCultureAttribute> для указания языка и региональных параметров, если ресурсы во вспомогательной сборке.
- Используйте <xref:System.Resources.NeutralResourcesLanguageAttribute> для указания *нейтрального языка и региональных параметров* сборки, если ресурсы находятся в той же сборки в коде.

> [!IMPORTANT]
> Если значение языка и региональных параметров отличное от культуры на основе английского, данное правило анализа кода автоматически отключается.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Это безопасно подавить предупреждение из этого правила, если обе части составного слова распознаются словарем и предполагается использование двух слов.

Можно также добавить составные слова в пользовательский словарь для проверки орфографии. Слова в пользовательский словарь не вызывают нарушений. Дополнительные сведения см. в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Связанные правила

- [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>См. также

- [Соглашения о написании прописными буквами](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Правила именования](/dotnet/standard/design-guidelines/naming-guidelines)