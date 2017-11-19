---
title: "CA2204: Литералы должны иметь правильное правописание | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords: CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7fca8484b3231a92ab3a425c4661229236833642
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: литералы должны иметь правильное написание
|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод передает строковый литерал, используется в параметре или свойство, требующее локализованную строку и этот строковый литерал содержит одно или несколько слов, не распознаваемых библиотекой системы проверки правописания Майкрософт.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило проверяет строковый литерал, который передается как значение параметра или свойства, когда один или несколько из следующих условий верно:  
  
-   <xref:System.ComponentModel.LocalizableAttribute> Атрибута параметра или свойства задано значение true.  
  
-   Имя параметра или свойства содержит «Текст», «Сообщение» или «Заголовок».  
  
-   Строковый параметр, который передается методу Console.Write или Console.WriteLine называется «value» или «format».  
  
 Это правило анализирует литеральную строку по словам, маркирование составных слов и проверяет правильность написания всех слов и лексем. Сведения об алгоритме анализа см. в разделе [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 По умолчанию используется английский (en) версия средства проверки орфографии.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, исправьте написание слова или добавьте это слово в пользовательский словарь. Сведения об использовании пользовательских словарей см. в разделе [как: Настройка словаря анализа кода](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Правильно написанные слова сокращают время обучения, необходимых для новых библиотек программного обеспечения.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1704: идентификаторы должны иметь правильное правописание](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: соблюдайте правильность написания строк ресурсов](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)