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
ms.openlocfilehash: b5e078fc1bb7fe247d541e7695e98c2de76c2466
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544070"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704. Идентификаторы должны иметь правильное правописание
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
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

- Внедренные амперсанды удаляются. Например, для&разбиваются на "формат".

  По умолчанию используется английская версия (EN) средства проверки орфографии. Другие языковые словари в настоящее время недоступны.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, исправьте написание слова или добавьте слово в пользовательский словарь с именем CustomDictionary.xml. Поместите словарь в каталог установки средства, каталог проекта или в каталог, связанный с инструментом в профиле пользователя (%USERPROFILE%\Application Data \\ ...). Сведения о том, как добавить пользовательский словарь в проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , см. в разделе [как настроить словарь анализа кода.](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

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
 [CA2204. Литералы должны иметь правильное правописание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703. Строки ресурса должны иметь правильное правописание](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709. Идентификаторы должны иметь правильное сочетание прописных и строчных букв](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707. Идентификаторы не должны содержать символы подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726. Используйте предпочтительные термины](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>См. также:
 [Практическое руководство. Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
