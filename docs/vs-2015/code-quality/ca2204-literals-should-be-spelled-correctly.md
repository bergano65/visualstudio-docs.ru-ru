---
title: 'CA2204: литералы должны быть написаны правильно | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d3e94f308936f898e555b1ad38e6a9d50051a276
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659540"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: литералы должны иметь правильное написание
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|литералсшаулдбеспелледкорректли|
|CheckId|CA2204|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод передает литеральную строку, которая используется в параметре или свойстве, для которого требуется локализованная строка, а литеральная строка содержит одно или несколько слов, не распознаваемых библиотекой средства проверки орфографии Майкрософт.

## <a name="rule-description"></a>Описание правила
 Это правило проверяет литеральную строку, которая передается как значение в параметр или свойство, если выполняется одно или несколько из следующих условий.

- Атрибут <xref:System.ComponentModel.LocalizableAttribute> параметра или свойства имеет значение true.

- Имя параметра или свойства содержит "Text", "Message" или "Caption".

- Имя строкового параметра, передаваемого методу Console. Write или Console. WriteLine — либо value, либо Format.

  Это правило анализирует литеральную строку в словах, размечая составные слова и проверяет орфографию каждого слова или маркера. Дополнительные сведения о алгоритме синтаксического анализа см. в разделе [CA1704: идентификаторы должны быть написаны правильно](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  По умолчанию используется английская версия (EN) средства проверки орфографии.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, исправьте написание слова или добавьте слово в пользовательский словарь. Сведения о том, как использовать пользовательские словари, см. в разделе [инструкции. Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Правильное написание слов сокращает кривую обучения, необходимую для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила
 [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
