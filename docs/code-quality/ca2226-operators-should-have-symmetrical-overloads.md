---
title: CA2226. Перегрузки операторов должны быть симметричными
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d9e486d4193645335189c475fdd3ca220374d96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231440"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226. Перегрузки операторов должны быть симметричными

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Тип реализует оператор равенства или неравенства, но не реализует противоположный оператор.

По умолчанию это правило рассматривает только видимые извне типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Отсутствуют обстоятельства, в которых применимость или неравенство к экземплярам типа, а противоположный оператор не определен. Типы обычно реализуют оператор неравенства, возвращая отрицательное значение оператора равенства.

C# Компилятор выдает ошибку для нарушений этого правила.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте операторы равенства и неравенства или удалите существующий объект.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует. В противном случае тип будет работать не так, как если бы он соответствовал .NET.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca2226.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (использование). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Связанные правила

- [CA1046: Не перегружать оператор Equals в ссылочных типах](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225 Перегрузки операторов имеют именованные варианты](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224: Переопределять Equals при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Переопределять GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)