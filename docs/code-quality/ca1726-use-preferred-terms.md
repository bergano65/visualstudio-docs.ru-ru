---
title: CA1726. Используйте предпочтительные термины
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81364979092d2964c006aaefd29a5a3749565807
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931080"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726. Используйте предпочтительные термины

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое — для сборок<br /><br /> Не критическое — при возникновении в параметрах типов|

## <a name="cause"></a>Причина

Имя видимого снаружи идентификатора включает термин, для которого существует другой предпочтительный термин. Или, если имя содержит термин Flag или Flags.

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