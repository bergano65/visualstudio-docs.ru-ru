---
title: CA1726. Используйте предпочитаемые термины | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67dab4c732faa04af44800f740d78c4ce4f9dc80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143160"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726. Используйте предпочтительные термины
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio, см. в разделе [CA1726: Используйте предпочитаемые термины](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms).  
  
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое — для сборок<br /><br /> Не критическое — при возникновении в параметрах типов|  
  
## <a name="cause"></a>Причина  
 Имя видимого снаружи идентификатора включает термин, для которого существует другой предпочтительный термин. Кроме того имя содержит термин Flag или Flags.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило выполняет синтаксический анализ идентификатора в токены. Каждая отдельная лексема и каждая последовательность двух лексем сравнивается с условиями, встроенные в правило и в разделе не рекомендуемые к использованию всех пользовательских словарей. В следующей таблице показаны условия, которые встроены в правило и их предпочтительный альтернатив.  
  
|Устаревшее название|Предпочтительный термин|  
|-------------------|--------------------|  
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` или `Flags`|Есть слово для замены. Не используется.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, замените термин предпочтительный термин для альтернативных.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила, только в том случае, если имя идентификатора является преднамеренным и посвящен исходный термин вместо предпочтительный термин.  
  
## <a name="related-rules"></a>Связанные правила  
 [Предупреждения именования](../code-quality/naming-warnings.md)
