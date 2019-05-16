---
title: CA1702. Составные слова должны иметь правильный регистр | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 91a3945c6ef212ba664119a822123f326cdefc5c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676396"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702. Для сложных слов следует использовать правильный регистр
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio, см. в разделе [CA1702: Составные слова должны иметь правильный регистр](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly).  
  
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое — при возникновении в сборках.<br /><br /> Не критическое — при возникновении в параметрах типа.|  
  
## <a name="cause"></a>Причина  
 Имя идентификатора состоит из нескольких слов и по крайней мере одно из слов быть составным словом в неправильном регистре.  
  
## <a name="rule-description"></a>Описание правила  
 Имя идентификатора разбивается на слова, с учетом регистра. Каждое смежных сочетание двух слов проверяется библиотекой проверки орфографии Майкрософт. Если он был распознан, идентификатор создает нарушение правила. Примеры составных словах, вызывать нарушение: «Контрольная сумма» и «MultiPart», должны иметь правильный регистр как «Контрольная сумма» и «Multipart», соответственно. Из-за предыдущего общего использования, несколько исключений встроены в правило, и помечаются несколько слов, например «Toolbar» и «Filename», который должны иметь правильный регистр определенных слов (в данном случае «ToolBar» и «FileName»).  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Измените имя, таким образом, чтобы регистр.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила, если обе части составного слова распознаются словарем и предполагается использовать два слова.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1701: Составных словах строк ресурса должны иметь правильный регистр](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>См. также  
 [Рекомендации по именованию](https://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [Соглашения о написании прописными буквами](https://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)
