---
title: CA1704. Идентификаторы должны иметь правильное правописание
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c39f744556968ff279b3e3e7e9eb923ec069ebc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954413"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704. Идентификаторы должны иметь правильное правописание

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Имя идентификатора содержит одно или несколько слов, не распознаваемых библиотекой средства проверки орфографии Майкрософт. Это правило не проверить конструкторы или с особыми именами членов, таких как get и настроить доступа к свойствам.

## <a name="rule-description"></a>Описание правила

Это правило анализирует идентификатор на лексемы и проверяет правильность каждого токена. Синтаксического анализа алгоритм выполняет следующие преобразования:

- Прописные буквы начать новый маркер. Например MyNameIsJoe преобразуется в «Мой», «Name», «Is», «Joe».

- Для нескольких прописных букв последняя прописная буква начинается новый маркер. Например GUIEditor преобразуется в «Графическим интерфейсом пользователя», «Редактор».

- Удаляются начальные и конечные апострофы. Например «отправитель» преобразуется в «sender».

- Символы подчеркивания обозначают окончание маркер и будут удалены. Например, Hello_world преобразуется в «Hello», «world».

- Внедренные знаки амперсанда удаляются. Например, for&mat преобразуется в "format".

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

Чтобы устранить нарушение данного правила, исправьте Правописание слова или добавьте это слово в пользовательский словарь.

### <a name="to-add-words-to-a-custom-dictionary"></a>Для добавления слова в пользовательский словарь

Имя XML-файле пользовательского словаря *CustomDictionary.xml*. Поместите этот словарь в каталоге установки средства в каталоге проекта или в каталоге, связанный со средством в профиле пользователя (*%USERPROFILE%\Application данных\\...* ). Узнайте, как добавить пользовательский словарь в проект в Visual Studio, см. в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Добавьте слова, которые не должны вызывать нарушение пути словарь/слова/распознаны.

- Добавьте слова, которые должны вызывать нарушение пути словарь/слова или нераспознано.

- Добавьте слова, которые должны быть отмечены как устаревшие пути словарь/слова или не рекомендуемые к использованию. См. в разделе связанные правила [CA1726: Используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md) Дополнительные сведения.

- Добавьте исключения для правила определения регистра аббревиатура в словарь/акронимов/CasingExceptions путь.

Ниже приведен пример структуры файла пользовательского словаря:

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

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Отключайте предупреждение из этого правила, только в том случае, если слово преднамеренно нарушена, и слово применяется к ограниченному набору библиотеки. Правильно слов с ошибками упростить процесс обучения, которая необходима для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила

- [CA2204: Литералы должны иметь правильное правописание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Строки ресурсов должны иметь правильное правописание](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>См. также

- [Практическое руководство. Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
