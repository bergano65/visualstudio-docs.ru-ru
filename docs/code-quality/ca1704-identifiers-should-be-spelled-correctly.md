---
title: 'CA1704: идентификаторы должны иметь правильное написание'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 710e18f4ce8199c76c34683c510d3a64160544e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916912"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: идентификаторы должны иметь правильное написание

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Имя идентификатора содержит одно или несколько слов, не распознаваемых библиотекой системы проверки правописания Майкрософт. Это правило не проверьте конструкторы и члены с особыми именами, например get и задайте свойствам.

## <a name="rule-description"></a>Описание правила

Это правило анализирует идентификатор на лексемы и проверку орфографии для каждого маркера. Алгоритм синтаксического анализа выполняет следующие преобразования:

- Прописные буквы запустить новый маркер. Например MyNameIsJoe преобразуется в «My», «Name», «Равно», «Joe».

- Для нескольких прописных букв последняя прописная буква является началом нового токена. Например GUIEditor преобразуется в «Графическим интерфейсом пользователя», «Редактор».

- Удаляются начальные и конечные апострофы. Например «отправителя» преобразуется в «sender».

- Символы подчеркивания обозначают окончание маркер и будут удалены. Например, Hello_world преобразуется в «Hello», «world».

- Внедренные амперсанды удаляются. Например, for&mat преобразуется в "format".

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

Чтобы устранить нарушение данного правила, исправьте написание слова или добавьте это слово в пользовательский словарь.

### <a name="to-add-words-to-a-custom-dictionary"></a>Добавление слова в пользовательский словарь

Имя XML-файл пользовательского словаря *CustomDictionary.xml*. Поместите этот словарь в каталог установки средства в каталоге проекта или в каталог, связанный со средством в профиле пользователя (*%USERPROFILE%\Application данные\\...* ). Дополнительные сведения о добавлении пользовательского словаря в проект в Visual Studio, в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Добавление слова, которые не должны быть причиной нарушения в словарь, слова или распознаны пути.

- Добавление слова, которые должны вызывать нарушение пути словаря, слова или нераспознано.

- Добавление слова, которые должны быть отмечены как устаревшие пути словаря, слова или устарел. См. в разделе связанные правила [CA1726: используйте предпочтительные термины](../code-quality/ca1726-use-preferred-terms.md) для получения дополнительной информации.

- Добавьте исключения для правила определения регистра для сокращения в словарь, сокращений и CasingExceptions путь.

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

Отключайте предупреждение из этого правила только в том случае, если слова преднамеренно нарушена и это слово применяется ограниченный набор библиотеки. Правильно написанные слова сокращают время на изучение, необходимой для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила

- [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>См. также

- [Практическое руководство. Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
