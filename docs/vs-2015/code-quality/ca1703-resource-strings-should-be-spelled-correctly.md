---
title: CA1703. Строки ресурсов должны иметь правильное правописание | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1ff5a2600a4f40673f7d38dfe551ab9ac8cfe29
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980107"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703. Строки ресурса должны иметь правильное правописание
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 По умолчанию используется английский (en) версия средства проверки орфографии.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, используйте полные слова написаны правильно или добавьте слова в пользовательский словарь. Сведения о том, как использовать настраиваемые словари, см. в разделе [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Правильно написанные слова сокращают время, необходимое для получения новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила
 [CA1701: Составных словах строк ресурса должны иметь правильный регистр](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Литералы должны иметь правильное правописание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
