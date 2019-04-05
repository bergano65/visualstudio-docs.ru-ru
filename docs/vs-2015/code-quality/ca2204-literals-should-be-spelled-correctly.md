---
title: CA2204. Литералы должны иметь правильное правописание | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a08cb7cee2af51ade4b94dbf675ff83d7da456e2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992230"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204. Литералы должны иметь правильное правописание
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод передает текстовую строку, которая используется в параметре или свойство, которое требует локализованную строку и строковый литерал содержит одно или несколько слов, не распознаваемых библиотекой средства проверки орфографии Майкрософт.

## <a name="rule-description"></a>Описание правила
 Это правило проверяет строковый литерал, который передается как значение параметра или свойства, если один или несколько из следующих условий верно:

- <xref:System.ComponentModel.LocalizableAttribute> Установлен атрибут параметра или свойства в значение true.

- Имя параметра или свойства содержит «Text», «Message» или «Заголовок».

- Строковый параметр, который передается методу Console.Write и Console.WriteLine называется «value» или «format».

  Это правило анализирует литеральную строку на слова, маркирование составных слов и проверяет правильность написания всех слов и лексем. Сведения об алгоритме анализа см. в разделе [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  По умолчанию используется английский (en) версия средства проверки орфографии.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, исправьте Правописание слова или добавьте это слово в пользовательский словарь. Сведения о том, как использовать настраиваемые словари, см. в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Правильно слов с ошибками упростить процесс обучения, необходимые для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила
 [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Строки ресурсов должны иметь правильное правописание](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
