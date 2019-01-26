---
title: CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: bf671e8c948f4554225278982c4db794fedb974d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023383"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса

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

## <a name="change-the-dictionary-language"></a>Изменить язык словаря

По умолчанию используется английский (en) версия средства проверки орфографии. Если вы хотите изменить язык проверки орфографии, это можно сделать путем добавления одного из следующих атрибутов для вашей *AssemblyInfo.cs* или *AssemblyInfo.vb* файла:

- Используйте <xref:System.Reflection.AssemblyCultureAttribute> для указания языка и региональных параметров, если ресурсы располагаются во вспомогательной сборке.
- Используйте <xref:System.Resources.NeutralResourcesLanguageAttribute> для указания *нейтрального языка и региональных параметров* Если ресурсы располагаются в той же сборке, что и код сборки.

> [!IMPORTANT]
> Если значение языка и региональных параметров, было присвоено имя, отличное от культуру английского языка, данное правило анализа кода автоматически отключается.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если обе части составного слова распознаются словарем и предполагается использовать два слова.

Можно также добавить составных слов в пользовательский словарь для проверки орфографии. Слова в пользовательский словарь не вызывают нарушений. Дополнительные сведения см. в разделе [Как Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Связанные правила

- [CA1702: Составные слова должны иметь правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>См. также

- [Соглашения о написании прописными буквами](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Правила именования](/dotnet/standard/design-guidelines/naming-guidelines)