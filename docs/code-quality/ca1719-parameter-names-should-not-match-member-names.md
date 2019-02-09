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
ms.openlocfilehash: 001983bf9ca182f89587b23e04828b93d12d98f1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953988"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719. Имена параметров не должны совпадать с именами членов

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя видимого элемента соответствует при сравнении без учета регистра, имя одного из своих параметров.

## <a name="rule-description"></a>Описание правила
 Имя параметра должно передавать смысловое значение параметра, а имя члена — смысловое значение члена. Они могут совпадать лишь в очень редких случаях. Присвоение параметру имени содержащего его члена кажется неестественным и затрудняет использование библиотеки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя параметра, которое не соответствует имени члена.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для разработки новых приложений, не известные сценарии возникнуть, когда необходимо подавить предупреждение из этого правила. Для доставки библиотек, возможно подавить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1709: Идентификаторы должны иметь правильный регистр](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Идентификаторы должны отличаться регистром](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Идентификаторы не должны содержать знак подчеркивания](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)