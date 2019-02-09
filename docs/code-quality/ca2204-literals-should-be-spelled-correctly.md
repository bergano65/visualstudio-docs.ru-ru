---
title: CA2204. Литералы должны иметь правильное правописание
ms.date: 03/28/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82146c2ac997a0202c20e15492becb89a293f427
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949451"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204. Литералы должны иметь правильное правописание

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Строковый литерал передается в качестве аргумента для параметра локализуемого или локализуемое свойство, и строка содержит одно или несколько слов, не распознаваемых библиотекой средства проверки орфографии Майкрософт.

## <a name="rule-description"></a>Описание правила

Это правило проверяет строковый литерал, который передается как значение параметра или свойства, если один или несколько из следующих условий верно:

- <xref:System.ComponentModel.LocalizableAttribute> Установлен атрибут параметра или свойства в значение true.

- Имя параметра или свойства содержит «Text», «Message» или «Заголовок».

- Имя строковой переменной, передаваемый <xref:System.Console.Write%2A> или <xref:System.Console.WriteLine> метод является «value» или «format».

Это правило анализирует литеральную строку на слова, маркирование составных слов и проверяет правильность каждого слово или токен. Сведения об алгоритме анализа см. в разделе [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Язык

Средство проверки орфографии в настоящее время проверяет только к словарям на основе английского языка и региональных параметров. Язык и региональные параметры проекта в файле проекта, можно изменить, добавив **CodeAnalysisCulture** элемент.

Пример:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Если значение языка и региональных параметров, было присвоено имя, отличное от культуру английского языка, данное правило анализа кода автоматически отключается.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение данного правила, исправьте Правописание слова или добавьте это слово в пользовательский словарь. Сведения о том, как использовать настраиваемые словари, см. в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует. Правильно слов с ошибками упростить процесс обучения, необходимые для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила

- [CA1704: Идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Строки ресурсов должны иметь правильное правописание](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)