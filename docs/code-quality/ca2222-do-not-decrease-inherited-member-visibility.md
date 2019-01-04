---
title: CA2222. Не уменьшайте видимость наследуемого члена
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 71b4bd27b7c2258e508f02c7c4e88a516c370209
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911969"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222. Не уменьшайте видимость наследуемого члена

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Закрытый метод в незапечатанный тип имеет подпись, идентичный открытый метод, объявленный в базовом типе. Закрытый метод не является окончательным.

## <a name="rule-description"></a>Описание правила

Не изменяйте модификатор доступа для унаследованных членов. Если сделать унаследованный член закрытым, то доступ вызывающих объектов к реализации метода базового класса все равно не будет запрещен. Если сделать закрытый член и тип не запечатан, наследуемые типы могут вызывать последнюю открытую реализацию метода в иерархии наследования. Если необходимо изменить модификатор доступа, метод должен быть помечен как окончательный, или его тип должны быть запечатаны, чтобы предотвратить переопределение метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените доступ к быть отличным от private. Кроме того если ее поддерживает язык программирования, можно сделать метод окончательной.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В следующем примере тип, который нарушает это правило.

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]