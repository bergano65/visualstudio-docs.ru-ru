---
title: CA1707. Идентификаторы не должны содержать символы подчеркивания
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb7fc19f90b7f0cd329dd1cff972d08c2052b055
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951382"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707. Идентификаторы не должны содержать символы подчеркивания

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое — при возникновении на сборки<br /><br /> Не критическое — при возникновении на параметры типа|

## <a name="cause"></a>Причина

Имя идентификатора содержит символ подчеркивания (\_) символов.

## <a name="rule-description"></a>Описание правила

По соглашению имена идентификаторов не содержат символ подчеркивания (\_) символов. Это правило проверяет пространства имен, типов, членов и параметров.

Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Удалите все знаки подчеркивания из имени.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила

- [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
