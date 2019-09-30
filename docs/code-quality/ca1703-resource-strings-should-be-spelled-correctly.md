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
ms.openlocfilehash: edd3945953a07b10aee5c2690a25aafe446e2c10
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234327"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703. Строки ресурса должны иметь правильное правописание

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Категория|Microsoft. Naming|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Строка ресурса содержит одно или несколько слов, не распознанных библиотекой системы проверки правописания Майкрософт.

## <a name="rule-description"></a>Описание правила

Это правило выполняет синтаксический анализ строки ресурса в словах (размечающие составные слова) и проверяет орфографию каждого слова или маркера. Дополнительные сведения о алгоритме синтаксического анализа см [. в разделе CA1704: Идентификаторы должны быть написаны правильно](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, используйте полные слова, написанные правильно, или добавьте слова в пользовательский словарь. Сведения о том, как использовать пользовательские словари, [см. в разделе CA1704: Идентификаторы должны быть написаны правильно](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Изменение языка словаря

По умолчанию используется английская версия (EN) средства проверки орфографии. Если вы хотите изменить язык средства проверки орфографии, это можно сделать, добавив в файл *AssemblyInfo.CS* или *AssemblyInfo. vb* один из следующих атрибутов:

- Используйте <xref:System.Reflection.AssemblyCultureAttribute> , чтобы указать язык и региональные параметры, если ресурсы находятся во вспомогательной сборке.
- Используйте <xref:System.Resources.NeutralResourcesLanguageAttribute> , чтобы указать *нейтральную культуру* сборки, если ресурсы находятся в той же сборке, что и код.

> [!IMPORTANT]
> Если для языка и региональных параметров задано значение, отличное от английского языка и региональных параметров, это правило анализа кода автоматически отключается.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует. Правильно написанные слова сокращают время, необходимое для изучения новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила

- [CA1701 В составных словах строк ресурсов следует указывать правильный регистр](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704 Идентификаторы должны быть написаны правильно](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Литералы должны быть написаны правильно](../code-quality/ca2204-literals-should-be-spelled-correctly.md)