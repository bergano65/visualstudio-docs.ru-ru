---
title: CA1704. Идентификаторы должны иметь правильное правописание
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa04ca237134c1947b5c58b921f87f32a1ecfb16
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234296"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704. Идентификаторы должны иметь правильное правописание

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Имя идентификатора содержит одно или несколько слов, не распознаваемых библиотекой проверки орфографии Майкрософт. Это правило не проверяет конструкторы или элементы с особыми именами, такие как методы доступа get и Set.

## <a name="rule-description"></a>Описание правила

Это правило анализирует идентификатор на токены и проверяет правописание каждого маркера. Алгоритм анализа выполняет следующие преобразования:

- Прописные буквы начинают новый маркер. Например, Минамеисжое размечается как "My", "Name", "-", "Джо".

- Для нескольких прописных букв последняя прописная буква запускает новый маркер. Например, Гуиедитор размечается как "GUI", "редактор".

- Начальные и конечные апострофы удаляются. Например, "sender" размечается как "sender".

- Знаки подчеркивания обозначают конец маркера и удаляются. Например, Hello_world размечается на "Hello", "World".

- Внедренные амперсанды удаляются. Например, для & разбиваются на "формат".

## <a name="language"></a>Язык

В настоящее время средство проверки орфографии проверяет только словари региональных параметров на основе английского языка. Вы можете изменить язык и региональные параметры проекта в файле проекта, добавив элемент **кодеаналисискултуре** .

Например:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Если для языка и региональных параметров задано значение, отличное от английского языка и региональных параметров, это правило анализа кода автоматически отключается.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, исправьте написание слова или добавьте слово в пользовательский словарь.

### <a name="to-add-words-to-a-custom-dictionary"></a>Добавление слов в пользовательский словарь

Назовите пользовательский словарь XML-файл *кустомдиктионари. XML*. Поместите словарь в каталог установки средства, каталог проекта или в каталог, связанный с инструментом в профиле пользователя ( *%UserProfile%\Application Data\\...* ). Сведения о том, как добавить пользовательский словарь в проект в Visual Studio, см. [в разделе как Настройка словаря](../code-quality/how-to-customize-the-code-analysis-dictionary.md)анализа кода.

- Добавьте слова, которые не должны вызывать нарушение по словарю/словам/распознанному пути.

- Добавьте слова, которые должны привести к нарушению по словарю или словам/нераспознанному пути.

- Добавьте слова, которые должны быть помечены как устаревшие, в разделе Словари/слова/устаревший путь. См. раздел [связанных правил CA1726: Используйте предпочтительные](../code-quality/ca1726-use-preferred-terms.md) термины для получения дополнительных сведений.

- Добавьте исключения в правила регистра акронимов в словарь, акронимы или путь Касинжексцептионс.

Ниже приведен пример структуры файла пользовательского словаря.

```xml
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Отключать предупреждение из этого правила следует только в том случае, если слово намеренно написано неправильно, а слово применяется к ограниченному набору библиотеки. Правильное написание слов сокращает кривую обучения, необходимую для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила

- [CA2204: Литералы должны быть написаны правильно](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703 Строки ресурсов должны быть написаны правильно](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709 Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Идентификаторы должны отличаться более чем регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707 Идентификаторы не должны содержать знаки подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726 Использовать предпочтительные термины](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>См. также

- [Практическое руководство. настройке словаря для анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
