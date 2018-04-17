---
title: 'CA1703: Строки ресурсов должны иметь правильное правописание | Документы Microsoft'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbd0fdccc9ee57223a6684b9caac191f1705c91c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, используйте полные слова, которые написаны правильно, или добавьте слова в пользовательский словарь. Сведения об использовании пользовательских словарей см. в разделе [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Изменить язык словаря

По умолчанию используется английский (en) версия средства проверки орфографии. Если вы хотите изменить язык проверки орфографии, это можно сделать, добавив один из следующих атрибутов к вашей *AssemblyInfo.cs* или *AssemblyInfo.vb* файла:

- Используйте <xref:System.Reflection.AssemblyCultureAttribute> для указания языка и региональных параметров, если ресурсы во вспомогательной сборке.
- Используйте <xref:System.Resources.NeutralResourcesLanguageAttribute> для указания *нейтрального языка и региональных параметров* сборки, если ресурсы находятся в той же сборки в коде.

> [!IMPORTANT]
> Если значение языка и региональных параметров отличное от культуры на основе английского, данное правило анализа кода автоматически отключается.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Правильно написанные слова сокращают время, необходимое для получения новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила

- [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)