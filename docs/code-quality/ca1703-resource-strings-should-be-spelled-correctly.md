---
title: CA1703. Строки ресурса должны иметь правильное правописание
ms.date: 03/28/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2643ff7cb8ce401462be7e5c1e52d5f985896f3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546275"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703. Строки ресурса должны иметь правильное правописание

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Категория|Microsoft.Naming|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Строка ресурса содержит одно или несколько слов, не распознанных библиотекой системы проверки правописания Майкрософт.

## <a name="rule-description"></a>Описание правила

Это правило анализирует строку ресурса на слова (маркирование составных слов) и проверяет правильность написания всех слов и лексем. Сведения об алгоритме анализа см. в разделе [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, используйте полные слова написаны правильно или добавьте слова в пользовательский словарь. Сведения о том, как использовать настраиваемые словари, см. в разделе [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Изменить язык словаря

По умолчанию используется английский (en) версия средства проверки орфографии. Если вы хотите изменить язык проверки орфографии, это можно сделать путем добавления одного из следующих атрибутов для вашей *AssemblyInfo.cs* или *AssemblyInfo.vb* файла:

- Используйте <xref:System.Reflection.AssemblyCultureAttribute> для указания языка и региональных параметров, если ресурсы располагаются во вспомогательной сборке.
- Используйте <xref:System.Resources.NeutralResourcesLanguageAttribute> для указания *нейтрального языка и региональных параметров* Если ресурсы располагаются в той же сборке, что и код сборки.

> [!IMPORTANT]
> Если значение языка и региональных параметров, было присвоено имя, отличное от культуру английского языка, данное правило анализа кода автоматически отключается.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Правильно написанные слова сокращают время, необходимое для получения новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила

- [CA1701: Составных словах строк ресурса должны иметь правильный регистр](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Литералы должны иметь правильное правописание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)