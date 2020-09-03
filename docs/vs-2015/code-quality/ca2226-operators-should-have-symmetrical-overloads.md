---
title: 'CA2226: операторы должны иметь симметричные перегрузки | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 430a8d3cfd3b8ced45b60bd9dc70211711886d43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540573"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226. Перегрузки операторов должны быть симметричными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип реализует оператор равенства или неравенства, но не реализует противоположный оператор.

## <a name="rule-description"></a>Описание правила
 Отсутствуют обстоятельства, в которых применимость или неравенство к экземплярам типа, а противоположный оператор не определен. Типы обычно реализуют оператор неравенства, возвращая отрицательное значение оператора равенства.

 Компилятор C# выдает ошибку для нарушений этого правила.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте операторы равенства и неравенства или удалите имеющийся.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Тип не будет работать способом, согласованным с [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="related-rules"></a>Связанные правила
 [CA1046. Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225. Для перегрузок операторов существуют варианты с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224. Переопределяйте Equals при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218. Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231. Перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
