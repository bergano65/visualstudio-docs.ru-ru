---
title: 'CA2204: литералы должны иметь правильное написание'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f86658978a105c1fa4f3c4602b5c838f4c80726
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: литералы должны иметь правильное написание

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Строковый литерал передается в качестве аргумента для параметра локализуемые или локализуемое свойство, и строка содержит одно или несколько слов, не распознаваемых библиотекой системы проверки правописания Майкрософт.

## <a name="rule-description"></a>Описание правила

Это правило проверяет строковый литерал, который передается как значение параметра или свойства, когда один или несколько из следующих условий верно:

- <xref:System.ComponentModel.LocalizableAttribute> Атрибута параметра или свойства задано значение true.

- Имя параметра или свойства содержит «Текст», «Сообщение» или «Заголовок».

- Имя строковой переменной, передаваемое <xref:System.Console.Write%2A> или <xref:System.Console.WriteLine> метод: «значение» или «format».

Это правило анализирует литеральную строку по словам, маркирование составных слов и проверку орфографии для каждого слова или маркер. Сведения об алгоритме анализа см. в разделе [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Язык

Проверка орфографии в настоящее время проверяет только к словарям на основе английского языка и региональных параметров. Язык и региональные параметры проекта в файле проекта, можно изменить, добавив **CodeAnalysisCulture** элемента.

Пример:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Если значение языка и региональных параметров отличное от культуры на основе английского, данное правило анализа кода автоматически отключается.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение данного правила, исправьте написание слова или добавьте это слово в пользовательский словарь. Сведения об использовании пользовательских словарей см. в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Правильно написанные слова сокращают время обучения, необходимых для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила

- [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)