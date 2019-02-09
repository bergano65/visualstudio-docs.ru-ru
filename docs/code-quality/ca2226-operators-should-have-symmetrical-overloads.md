---
title: CA2226. Перегрузки операторов должны быть симметричными
ms.date: 11/04/2016
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
ms.openlocfilehash: 6264b440df01e02019938eb0f742cb9789fd4f5d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931108"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226. Перегрузки операторов должны быть симметричными

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип реализует оператор равенства или неравенства, но не реализует противоположный оператор.

## <a name="rule-description"></a>Описание правила
 Существуют ни в коем случае равенства или неравенства применимо к экземплярам типа, куда противоположный оператор не определен. Типы обычно реализуют оператор неравенства, возвращая инвертированное значение от оператора равенства.

 Компилятор C# выдает ошибку нарушения этого правила.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализовать как операторы равенства и неравенства, или удалите тот, который присутствует.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Тип не будет работать таким образом, согласуется с .NET Framework.

## <a name="related-rules"></a>Связанные правила
 [CA1046: Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Оператор дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)