---
title: 'CA1703: строки ресурсов должны быть написаны правильно | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9574ff022e0d5407b2683e5ba7a6b2e0cde5201e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669225"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: соблюдайте правильность написания строк ресурсов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Категория|Microsoft. Naming|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Строка ресурса содержит одно или несколько слов, не распознанных библиотекой системы проверки правописания Майкрософт.

## <a name="rule-description"></a>Описание правила
 Это правило выполняет синтаксический анализ строки ресурса в словах (размечающие составные слова) и проверяет орфографию каждого слова или маркера. Дополнительные сведения о алгоритме синтаксического анализа см. в разделе [CA1704: идентификаторы должны быть написаны правильно](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 По умолчанию используется английская версия (EN) средства проверки орфографии.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, используйте полные слова, написанные правильно, или добавьте слова в пользовательский словарь. Сведения об использовании пользовательских словарей см. в разделе [CA1704: идентификаторы должны быть написаны правильно](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Правильно написанные слова сокращают время, необходимое для изучения новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила
 [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
