---
title: CA1707. Идентификаторы не должны содержать символы подчеркивания
ms.date: 11/04/2016
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
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252570"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707. Идентификаторы не должны содержать символы подчеркивания

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft. Naming|
|Критическое изменение|Критическое — при возникновении сборок<br /><br /> Не критическое — при возникновении параметров типа|

## <a name="cause"></a>Причина:

Имя идентификатора содержит символ подчеркивания (\_).

## <a name="rule-description"></a>Описание правила

По соглашению имена идентификаторов не содержат символ подчеркивания (\_). Правило проверяет пространства имен, типы, члены и параметры.

Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Удалите все символы подчеркивания из имени.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не отключайте предупреждения для рабочего кода. Однако можно спокойно отключить это предупреждение для кода теста. Вы можете отключить предупреждения из этого правила, задав для его [серьезности](use-roslyn-analyzers.md#rule-severity) значение **None**. 

## <a name="related-rules"></a>Связанные правила

- @NO__T 0CA1709: Идентификаторы должны иметь правильный регистр @ no__t-0
- @NO__T 0CA1708: Идентификаторы должны отличаться более чем регистром @ no__t-0
