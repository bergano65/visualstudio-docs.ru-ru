---
title: "CA1704: идентификаторы должны иметь правильное написание | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1704: идентификаторы должны иметь правильное написание
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Имя идентификатора содержит одно или несколько слов, не распознаваемых библиотекой средств проверки орфографии Майкрософт.  Данное правило не распространяется на конструкторы и члены с особыми именами, например, методы установки или получения значения свойства.  
  
## Описание правила  
 Данное правило выполняет синтаксический анализ идентификатора, разбивает его на лексемы и проверяет орфографию каждой лексемы.  Алгоритм синтаксического анализа выполняет следующие преобразования.  
  
-   Прописная буква означает начало новой лексемы.  Например, идентификатор MyNameIsJoe разбивается на лексемы "My", "Name", "Is", "Joe".  
  
-   В случае нескольких прописных букв последняя прописная буква является началом нового токена.  Например, идентификатор GUIEditor разбивается на лексемы "GUI", "Editor".  
  
-   Апострофы в начале и конце идентификатора удаляются.  Например, 'sender' преобразуется в лексему "sender".  
  
-   Знаки нижнего подчеркивания считаются концом лексемы и удаляются.  Например, Hello\_world разбивается на лексемы "Hello", "world".  
  
-   Внедренные амперсанты удаляются.  Например, for&mat преобразуется в лексему "format".  
  
 По умолчанию используется англоязычная \("en"\) версия средства проверки орфографии.  В настоящее время доступны словари только для этих языков.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, исправьте правописания слова или добавьте это слово в пользовательский словарь с именем CustomDictionary.xml.  Поместите этот словарь в каталог установки средства проверки орфографии, каталог проекта или каталог, связанный со средством в профиле пользователя \(%USERPROFILE%\\Application Data\\...\).  Сведения о добавлении пользовательского словаря в проект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] см. в разделе [Практическое руководство. Настройка словаря анализа кода](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
  
-   Добавьте слова, которые не должны вызывать нарушения, в раздел Dictionary\/Words\/Recognized.  
  
-   Добавьте слова, которые должны вызывать нарушения, в раздел Dictionary\/Words\/Unrecognized.  
  
-   Добавьте слова, которые должны быть помечены как устаревшие, в раздел Dictionary\/Words\/Deprecated.  Дополнительные сведения см. в разделе правил [CA1726: используйте предпочтительные термины](../code-quality/ca1726-use-preferred-terms.md).  
  
-   Добавьте исключения из правил использования прописных и строчных букв в акронимах в раздел Dictionary\/Acronyms\/CasingExceptions.  
  
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
  
## Отключение предупреждений  
 Предупреждения о нарушениях этого правила следует отключать только в том случае, если орфография слова преднамеренно нарушена и это слово применяется к ограниченному набору библиотеки.  Правильно написанные слова сокращают время, необходимое на освоение новых библиотек программного обеспечения.  
  
## Связанные правила  
 [CA2204: литералы должны иметь правильное написание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: идентификаторы должны отличаться не только регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: используйте предпочтительные термины](../code-quality/ca1726-use-preferred-terms.md)  
  
## См. также  
 [Практическое руководство. Настройка словаря анализа кода](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)