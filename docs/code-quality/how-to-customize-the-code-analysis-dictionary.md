---
title: 'Как: Настройка словаря анализа кода | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b2d60b2a187b7fccf4d5f564d9554badd5da9dec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Практическое руководство. Настройка словаря анализа кода
Анализ кода используется встроенный словарь для проверки идентификаторов в код на наличие ошибок в других соглашениям об именовании, орфографии и грамматические регистр [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] рекомендации. Можно создать пользовательский словарь XML-файл для добавления, удаления или изменения термины, сокращения и акронимы встроенных словарь.  
  
 Например, предположим, что код содержит класс с именем **DoorKnokker**. Анализ кода поможет идентифицировать имя как состоящий из двух слов: **дверцу** и **knokker**. Затем приведет к возникновению предупреждения, **knokker** написано правильно. Чтобы принудительно запустить анализ кода, чтобы распознать правописание, можно добавить термин **knokker** в пользовательский словарь.  
  
## <a name="to-create-a-custom-dictionary"></a>Создание пользовательского словаря  
 Создайте файл с именем **CustomDictionary.xml**.  
  
 Определите свои собственные слова, используя следующую структуру XML:  
  
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
  
## <a name="custom-dictionary-elements"></a>Пользовательский словарь элементов  
 Поведение словарь анализа кода можно изменить, добавив условия внутренний текст элемента в пользовательский словарь следующие элементы:  
  
-   [Словарь и слов и распознается/слов](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
-   [Словарь или слова или нераспознанный или Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
-   [Словарь или слова и не рекомендуется и выражение [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
-   [Словарь или слова или составного или выражение [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
-   [Словарь или слова или DiscreteExceptions или выражение](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
-   [Словарь или сокращений/CasingExceptions и сокращение](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Словарь и слов и распознается/слов  
 Чтобы включить термин в список терминов, распознаваемых при анализе кода как правильно написанные, добавьте этот термин во внутренний текст элемента Dictionary/Words/распознаны и Word. Термины в словарь и слов/Recognized/Word элементы не учитывают регистр.  
  
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
  
 Условия в словарь, слова или распознаны узлов применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Словарь или слова или нераспознанный или Word  
 Чтобы исключить термин из списка терминов, распознаваемых при анализе кода как правильно написанные, добавьте термин, чтобы исключить как внутренний текст элемента Dictionary/Words/нераспознано или Word. Условия в элементах Dictionary/Words/нераспознано/Word не учитывают регистр.  
  
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
  
 Условия в узле словаря, слова или нераспознано применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Словарь или слова и не рекомендуется и выражение [@PreferredAlternate]  
 Чтобы включить термин в список терминов, распознаваемых при анализе кода как устаревшие, добавьте этот термин во внутренний текст элемента словаря/слова или не рекомендуемые к использованию или выражение. Нерекомендуемый термин — это слово, которое написано правильно, но не должны использоваться.  
  
 Чтобы включить предлагаемый альтернативный термин в предупреждении, укажите альтернативного в атрибуте PreferredAlternate элемента Term. Если вы не хотите предложить альтернативный, можно оставить значение атрибута пустым.  
  
-   Устаревший термин в словарь и слов/элемент устарел или термин не учитывается регистр знаков.  
  
-   Значение атрибута PreferredAlternate учитывается регистр. Используйте Pascal регистр для составных альтернативных значений.  
  
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
  
 Условия в узле словаря, слова или устаревшие применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: используйте предпочитаемые термины](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Словарь или слова или составного или выражение [@CompoundAlternate]  
 Во встроенном словаре некоторые термины определяются как единый отдельный термин, а не как составной термин. Чтобы включить термин в список терминов, распознаваемых при анализе кода как составное слово и укажите правильный регистр символов для термина, добавьте этот термин во внутренний текст элемента словаря/слова или составного или выражение. В атрибуте CompoundAlternate элемента Term укажите отдельные слова, составляющих составной термин с прописной первую букву каждого слова (стиле Pascal). Обратите внимание, что выражения, заданного во внутреннем тексте автоматически добавляется в словарь, слова или DiscreteExceptions список.  
  
-   Устаревший термин в словарь и слов/элемент устарел или термин не учитывается регистр знаков.  
  
-   Значение атрибута PreferredAlternate учитывается регистр. Используйте Pascal регистр для составных альтернативных значений.  
  
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
  
 Условия в узле словаря, слова или составного применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Словарь или слова или DiscreteExceptions или выражение  
 Чтобы исключить термин в список терминов, распознаваемых при анализе кода как отдельный, отдельное слово термин установленном правила определения регистра для составных слов, добавьте термин во внутренний текст элемента словаря/Words/DiscreteExceptions/Term. Термин в словарь и слов/DiscreteExceptions/выражение элемента не учитывает регистр.  
  
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
  
 Условия в узле словаря, слова или DiscreteExceptions применяются для следующих правил анализа кода:  
  
-   [CA1701: соблюдайте правильность регистра в составных словах строк ресурса](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: для сложных слов следует использовать правильный регистр](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Словарь или сокращений/CasingExceptions и сокращение  
 Для включения в список терминов, которые анализа кода определяет, как написано правильно аббревиатура и указать, как сокращение термин установленном регистр правила для составных слов, добавьте этот термин во внутренний текст элемента словаря или сокращений/CasingExceptions / Элемент acronym. Сокращение в элемент словаря или сокращений/CasingExceptions/Acronym учитывается регистр.  
  
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
  
 Условия в узле словаря, сокращений и CasingExceptions применяются для следующих правил анализа кода:  
  
-   [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Для применения пользовательского словаря в проект  
  
1.  В **обозревателе решений**, используйте один из следующих процедур:  
  
2.  Чтобы добавить словарь в отдельный проект, щелкните правой кнопкой мыши имя проекта и нажмите кнопку **Добавление существующего элемента**. Укажите файл в **Добавление существующего элемента** диалоговое окно.  
  
3.  Чтобы добавить словарь, который является общим для двух или нескольких проектов, найдите файл для совместного использования в **Добавление существующего элемента** диалогового окна нажмите кнопку со стрелкой вниз на **добавить** и затем нажмите кнопку **добавить как ссылку** .  
  
4.  В **обозревателе решений**, щелкните правой кнопкой мыши **CustomDictionary.xml** имя файла и нажмите кнопку **свойства**.  
  
5.  Из **действие при построении** выберите **CodeAnalysisDictionary**.  
  
6.  Из **Копировать в выходной каталог** выберите **не Копировать**.