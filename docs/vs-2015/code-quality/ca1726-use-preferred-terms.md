---
title: 'CA1726: используйте предпочтительные термины | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f5d184684a6ec30c216b7274313905781843071b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671567"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: используйте предпочтительные термины
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю документацию по Visual Studio см. в разделе [CA1726: использование предпочтительных терминов](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms).

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое — при срабатывании в сборках<br /><br /> Не критическое — при срабатывании параметров типа|

## <a name="cause"></a>Причина
 Имя видимого снаружи идентификатора включает термин, для которого существует другой предпочтительный термин. Кроме того, имя включает в себя флаг или флаги.

## <a name="rule-description"></a>Описание правила
 Это правило анализирует идентификатор на токены. Каждый один маркер и каждая смежная двойная лексема сравниваются с терминами, встроенными в правило, и в нерекомендуемом разделе любых пользовательских словарей. В следующей таблице показаны термины, встроенные в правило, и их предпочтительные альтернативы.

|Устаревший термин|Предпочтительный срок|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` или `Flags`|Условия замены отсутствуют. Не используется.|
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
 Чтобы устранить нарушение этого правила, замените термин на предпочтительный альтернативный термин.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, только если имя идентификатора является преднамеренным и относится непосредственно к исходному термину вместо предпочтительного.

## <a name="related-rules"></a>Связанные правила
 [Предупреждения именования](../code-quality/naming-warnings.md)
