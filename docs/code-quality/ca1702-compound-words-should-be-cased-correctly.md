---
title: CA1702. Для сложных слов следует использовать правильный регистр
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f78ea4f44c48d2740df58def03a6335bce6637a2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942769"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702. Для сложных слов следует использовать правильный регистр

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое — при возникновении в сборках.<br /><br /> Не критическое — при возникновении в параметрах типа.|

## <a name="cause"></a>Причина

Имя идентификатора состоит из нескольких слов, и по крайней мере одно из них является составным словом в неправильном регистре.

## <a name="rule-description"></a>Описание правила

Имя идентификатора разбивается на слова, с учетом регистра. Каждое смежных сочетание двух слов проверяется библиотекой проверки орфографии Майкрософт. Если он был распознан, идентификатор создает нарушение правила. Примеры составных словах, вызывать нарушение: «Контрольная сумма» и «MultiPart», должны иметь правильный регистр как «Контрольная сумма» и «Multipart», соответственно. Из-за предыдущего общего использования, несколько исключений встроены в правило, и помечаются несколько слов, например «Toolbar» и «Filename», который должны иметь правильный регистр определенных слов (в данном случае «ToolBar» и «FileName»).

Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Измените имя, таким образом, чтобы регистр.

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

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если обе части составного слова распознаются словарем, и предполагается использовать два слова.

## <a name="related-rules"></a>Связанные правила

- [CA1701: Составных словах строк ресурса должны иметь правильный регистр](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>См. также

- [Правила именования](/dotnet/standard/design-guidelines/naming-guidelines)
- [Соглашения о написании прописными буквами](/dotnet/standard/design-guidelines/capitalization-conventions)