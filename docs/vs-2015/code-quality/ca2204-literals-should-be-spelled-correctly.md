---
title: 'CA2204: Литералы должны иметь правильное правописание | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 39d841fbfa9be3e3ee5764e986a9688ca4113caf
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591732"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: литералы должны иметь правильное написание
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2204: литералы должны иметь правильное правописание](https://docs.microsoft.com/visualstudio/code-quality/ca2204-literals-should-be-spelled-correctly).

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

-   <xref:System.ComponentModel.LocalizableAttribute> Установлен атрибут параметра или свойства в значение true.

-   Имя параметра или свойства содержит «Text», «Message» или «Заголовок».

-   Строковый параметр, который передается методу Console.Write и Console.WriteLine называется «value» или «format».

 Это правило анализирует литеральную строку на слова, маркирование составных слов и проверяет правильность написания всех слов и лексем. Сведения об алгоритме анализа см. в разделе [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 По умолчанию используется английский (en) версия средства проверки орфографии.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, исправьте Правописание слова или добавьте это слово в пользовательский словарь. Сведения о том, как использовать настраиваемые словари, см. в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Правильно слов с ошибками упростить процесс обучения, необходимые для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила
 [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)



