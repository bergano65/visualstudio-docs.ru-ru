---
title: CA1704. Идентификаторы должны иметь правильное правописание | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d77e5ffcb7cc6688ea07cd99760e79e8f92aeb43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991241"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704. Идентификаторы должны иметь правильное правописание
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

- Внедренные знаки амперсанда удаляются. Например, & mat преобразуется в «format».

  По умолчанию используется английский (en) версия средства проверки орфографии. Нет словари в настоящее время доступны.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, исправьте Правописание слова или добавьте это слово в пользовательский словарь, который называется CustomDictionary.xml. Поместите этот словарь в каталоге установки средства в каталоге проекта или в каталоге, связанный со средством в профиле пользователя (%USERPROFILE%\Application данных\\...). Чтобы узнать, как добавить пользовательский словарь в проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], см. в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Добавьте слова, которые не должны вызывать нарушение пути словарь/слова/распознаны.

- Добавьте слова, которые должны вызывать нарушение пути словарь/слова или нераспознано.

- Добавьте слова, которые должны быть отмечены как устаревшие пути словарь/слова или не рекомендуемые к использованию. См. в разделе связанные правила [CA1726: Используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)Дополнительные сведения.

- Добавьте исключения для правила определения регистра аббревиатура в словарь/акронимов/CasingExceptions путь.

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
 Отключайте предупреждение из этого правила, только в том случае, если слово преднамеренно нарушена, и слово применяется к ограниченному набору библиотеки. Правильно слов с ошибками упростить процесс обучения, которая необходима для новых библиотек программного обеспечения.

## <a name="related-rules"></a>Связанные правила
 [CA2204: Литералы должны иметь правильное правописание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: Строки ресурсов должны иметь правильное правописание](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: Используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>См. также
 [Практическое руководство. Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
