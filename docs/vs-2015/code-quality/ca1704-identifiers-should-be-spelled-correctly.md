---
title: 'CA1704: идентификаторы должны быть написаны правильно | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56ac5e60964621859c77bf53dc4f6c14480b4a83
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669239"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: идентификаторы должны иметь правильное написание
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя идентификатора содержит одно или несколько слов, не распознаваемых библиотекой проверки орфографии Майкрософт. Это правило не проверяет конструкторы или элементы с особыми именами, такие как методы доступа get и Set.

## <a name="rule-description"></a>Описание правила
 Это правило анализирует идентификатор на токены и проверяет правописание каждого маркера. Алгоритм анализа выполняет следующие преобразования:

- Прописные буквы начинают новый маркер. Например, Минамеисжое размечается как "My", "Name", "-", "Джо".

- Для нескольких прописных букв последняя прописная буква запускает новый маркер. Например, Гуиедитор размечается как "GUI", "редактор".

- Начальные и конечные апострофы удаляются. Например, "sender" размечается как "sender".

- Знаки подчеркивания обозначают конец маркера и удаляются. Например, Hello_world размечается на "Hello", "World".

- Внедренные амперсанды удаляются. Например, для & разбиваются на "формат".

  По умолчанию используется английская версия (EN) средства проверки орфографии. Другие языковые словари в настоящее время недоступны.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, исправьте написание слова или добавьте слово в пользовательский словарь с именем Кустомдиктионари. XML. Поместите словарь в каталог установки средства, каталог проекта или в каталог, связанный с инструментом в профиле пользователя (%USERPROFILE%\Application Data \\...). Чтобы узнать, как добавить пользовательский словарь в проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], см. раздел [как настроить словарь анализа кода.](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Добавьте слова, которые не должны вызывать нарушение по словарю/словам/распознанному пути.

- Добавьте слова, которые должны привести к нарушению по словарю или словам/нераспознанному пути.

- Добавьте слова, которые должны быть помечены как устаревшие, в разделе Словари/слова/устаревший путь. Дополнительные сведения см. в разделе о связанном правиле [CA1726: использование предпочтительных условий](../code-quality/ca1726-use-preferred-terms.md).

- Добавьте исключения в правила регистра акронимов в словарь, акронимы или путь Касинжексцептионс.

  Ниже приведен пример структуры файла пользовательского словаря.

```
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
 Отключать предупреждение из этого правила следует только в том случае, если слово намеренно написано неправильно, а слово применяется к ограниченному набору библиотеки. Правильное написание слов сокращает кривую обучения, необходимую для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила
 [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>См. также раздел
 [Практическое руководство. Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
