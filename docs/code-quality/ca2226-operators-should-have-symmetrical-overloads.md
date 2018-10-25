---
title: 'CA2226: перегрузки операторов должны быть симметричны'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8c872df976379a9bd20f28ceb9f4bf3eb376c8e8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900466"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: перегрузки операторов должны быть симметричны

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
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: для перезагрузок оператора существуют дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)