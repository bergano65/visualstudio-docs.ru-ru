---
title: 'Практическое: Настройка словаря анализа кода | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 345a46631e9f69c89af0e1d283c484ad71023821
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560038"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Практическое руководство. Настройка словаря анализа кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Настройка словаря анализа кода](https://docs.microsoft.com/visualstudio/code-quality/how-to-customize-the-code-analysis-dictionary).  
  
Анализ кода используется встроенный словарь для проверки идентификаторов в коде ошибок правописания, грамматические регистр и другие соглашения об именовании [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] рекомендации. Можно создать пользовательский словарь XML-файл, чтобы добавить, удалить или изменить условия, сокращений и акронимов встроенный словарь.  
  
 Например, предположим, что код содержит класс с именем **DoorKnokker**. Анализ кода будет идентифицировать имя как состоящий из двух слов: **дверь** и **knokker**. Он будет затем вызывать предупреждение, **knokker** написано правильно. Чтобы принудительно запустить анализ кода распознавалось, можно добавить термин **knokker** в пользовательский словарь.  
  
## <a name="to-create-a-custom-dictionary"></a>Для создания пользовательского словаря  
 Создайте файл с именем **CustomDictionary.xml**.  
  
 Задайте свои собственные слова, используя следующую структуру XML:  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>knokker</Word>  
         </Unrecognized>  
         <Recognized>  
            <Word></Word>  
         </Recognized>  
         <Deprecated>  
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
         </Compound>  
         <DiscreteExceptions>  
            <Term></Term>  
         </DiscreteExceptions>  
      </Words>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym></Acronym>  
         </CasingExceptions>  
      </Acronyms>  
   </Dictionary>  
```  
  
## <a name="custom-dictionary-elements"></a>Элементы пользовательского словаря  
 Поведение словарь анализа кода можно изменить, добавив условия как внутренний текст из следующих элементов в словарь:  
  
-   [Словарь и слова/распознан/слов](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [Словарь и слова или нераспознанный/слов](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [Словарь/слова/устаревшим/выражение [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [Словарь/слова/составной оператор или выражение [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [Словарь/слова/DiscreteExceptions/термин](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [Словарь/акронимов/CasingExceptions/аббревиатура](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Словарь и слова/распознан/слов  
 Чтобы включить термин в список терминов, которые анализа кода определяет, как правильно написанные, добавьте термин как внутренний текст элемента словаря и слова/распознаны/слов. Условия в элементах словаря и слова/распознаны/слов не учитывается.  
  
 **Пример**  
  
```  
<Dictionary>  
      <Words>  
         <Recognized>  
            <Word>knokker</Word>  
            ...  
         </Recognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Термины в словарь/слова/распознаны узлов применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Словарь и слова или нераспознанный/слов  
 Чтобы исключить термин из списка терминов, анализа кода определяет как неправильно написанные, добавьте термин для исключения как внутренний текст элемента словаря и слова/нераспознано/слов. Условия в элементах словаря и слова/нераспознано/слов не учитывается.  
  
 **Пример**  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>meth</Word>  
            ...  
         </Unrecognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Условия в узле словарь/слова/нераспознано применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Словарь/слова/устаревшим/выражение [@PreferredAlternate]  
 Чтобы включить термин в список терминов, которые анализа кода определяет, как устаревшие, добавьте термин как внутренний текст элемента словаря/слова или не рекомендуемые к использованию/Term. Нерекомендуемый термин — слово, которое написано правильно, но не следует использовать.  
  
 Чтобы включить предлагаемый альтернативный термин в предупреждении, предоставить этот альтернативный адрес в атрибуте PreferredAlternate элемента термин. Если вы не хотите предложить альтернативный вариант, можно оставить значение атрибута пустым.  
  
-   Устаревшие термин в словарь/слова или не рекомендуемые к использованию/термин элемент не является приложением с учетом регистра.  
  
-   Значение атрибута PreferredAlternate учитывается регистр. Используйте регистре Pascal для составных альтернативных значений.  
  
 **Пример**  
  
```  
<Dictionary>  
      <Words>  
         <Deprecated>  
            <Term PreferredAlternate="LogOn">login</Term>  
            ...  
         </Deprecated>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Условия в узле словарь/слова или не рекомендуемые к использованию применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Словарь/слова/составной оператор или выражение [@CompoundAlternate]  
 Встроенный словарь определяет некоторые термины, как единый отдельный термин, а не как составной термин. Чтобы включить термин в список терминов, которые анализа кода определяет как составное слово и укажите правильный регистр термина, добавьте термин как внутренний текст элемента словаря/слова/составной оператор или выражение. В атрибуте CompoundAlternate элемента Term укажите отдельные слова, составляющих составной термин с прописной первую букву каждого слова (верхнего регистра). Обратите внимание на то, что на срок, указанный во внутреннем тексте автоматически добавляется в список слов/словарь/DiscreteExceptions.  
  
-   Устаревшие термин в словарь/слова или не рекомендуемые к использованию/термин элемент не является приложением с учетом регистра.  
  
-   Значение атрибута PreferredAlternate учитывается регистр. Используйте регистре Pascal для составных альтернативных значений.  
  
 **Пример**  
  
```  
<Dictionary>  
      <Words>  
         <Compound>  
            <Term CompoundAlternate="CheckBox">checkbox</Term>  
            ...  
         </Compound>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Условия в узле словарь/слова/Compound применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Словарь/слова/DiscreteExceptions/термин  
 Чтобы исключить термин в список терминов, которые анализа кода определяет как один, дискретные word термин установленном правила учета регистра для составных слов, добавьте термин как внутренний текст элемента словаря/слова/DiscreteExceptions/Term. Термин в словарь/слова/DiscreteExceptions/выражение элемента не учитывается.  
  
 **Пример**  
  
```  
<Dictionary>  
      <Words>  
         <DiscreteExceptions>  
            <Term>checkbox</Term>  
            ...  
         </DiscreteExceptions>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Условия в узле словарь/слова/DiscreteExceptions применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Словарь/акронимов/CasingExceptions/аббревиатура  
 Чтобы включить аббревиатуру в список терминов, которые анализа кода определяет как написано правильно и указать работе аббревиатуры при проверке термина с учетом правил для составных слов, добавьте этот термин во внутренний текст элемента словаря/акронимов/CasingExceptions / Элемент. Сокращение в словарь/акронимов/CasingExceptions/элемент чувствителен к регистру.  
  
 **Пример**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 Условия в узле словарь/акронимов/CasingExceptions применяются для следующих правил анализа кода:  
  
-   [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Для применения пользовательского словаря в проект  
  
1.  В **обозревателе решений**, используйте один из следующих процедур:  
  
2.  Чтобы добавить словарь в отдельный проект, щелкните правой кнопкой мыши имя проекта и нажмите кнопку **добавить существующий элемент**. Укажите файл в **добавить существующий элемент** диалоговое окно.  
  
3.  Чтобы добавить словарь, который является общим для двух или нескольких проектов, найдите файл для совместного использования в **добавить существующий элемент** диалогового окна щелкните стрелку вниз на **добавить** а затем нажмите кнопку **добавить как ссылку** .  
  
4.  В **обозревателе решений**, щелкните правой кнопкой мыши **CustomDictionary.xml** имя файла и нажмите кнопку **свойства**.  
  
5.  Из **действие при построении** выберите **CodeAnalysisDictionary**.  
  
6.  Из **Копировать в выходной каталог** выберите **не Копировать**.



