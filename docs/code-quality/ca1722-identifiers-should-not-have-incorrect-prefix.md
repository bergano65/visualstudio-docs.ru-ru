---
title: CA1722. Идентификаторы не должны иметь неправильные префиксы
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5daf51cd8bef4910a327b8e261f15332ad6522da
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921612"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722. Идентификаторы не должны иметь неправильные префиксы

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Идентификатор имеет неверный префикс.

## <a name="rule-description"></a>Описание правила
В соответствии с соглашением об именовании, только некоторые элементы программирования могут иметь имена, которые начинаются с особого префикса.

Имена типов не имеют определенного префикса и не должны начинаться с "C". Это правило сообщает о нарушениях имен типов, таких как "Кмикласс", и не сообщает о нарушениях имен типов, таких как "Cache".

Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Такая согласованность сокращает курс обучения, необходимый для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана пользователями, обладающими опытом в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Удалите префикс из идентификатора.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
[CA1715 Идентификаторы должны иметь правильный префикс](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)