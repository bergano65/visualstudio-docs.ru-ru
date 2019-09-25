---
title: CA1719. Имена параметров не должны совпадать с именами членов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2aa55993758df24346b78eb4d9ad022014d9d81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233987"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719. Имена параметров не должны совпадать с именами членов

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Имя видимого извне элемента совпадает с именем одного из его параметров в сравнении без учета регистра.

## <a name="rule-description"></a>Описание правила
Имя параметра должно передавать смысловое значение параметра, а имя члена — смысловое значение члена. Они могут совпадать лишь в очень редких случаях. Присвоение параметру имени содержащего его члена кажется неестественным и затрудняет использование библиотеки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Выберите имя параметра, не совпадающее с именем члена.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для новой разработки нет известных сценариев, при которых необходимо отключить предупреждение из этого правила. Для доставки библиотек может потребоваться отключить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
[CA1709 Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708: Идентификаторы должны отличаться более чем регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707 Идентификаторы не должны содержать знаки подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)