---
title: CA2222. Не уменьшайте видимость наследуемого члена
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c737a30569ab4cd59931a3fca0e500ebe96e62de
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230984"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222. Не уменьшайте видимость наследуемого члена

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Частный метод в незапечатанном типе имеет сигнатуру, идентичную общедоступному методу, объявленному в базовом типе. Частный метод не является окончательным.

## <a name="rule-description"></a>Описание правила

Не изменяйте модификатор доступа для наследуемых членов. Если сделать унаследованный член закрытым, то доступ вызывающих объектов к реализации метода базового класса все равно не будет запрещен. Если член является закрытым и тип является незапечатанным, наследуемые типы могут вызывать последнюю открытую реализацию метода в иерархии наследования. Если необходимо изменить модификатор доступа, то либо метод должен быть помечен как Final, либо его тип должен быть запечатанным, чтобы предотвратить переопределение метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените доступ, не являющийся частным. Кроме того, если ваш язык программирования поддерживает его, можно сделать метод окончательным.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В следующем примере показан тип, нарушающий это правило.

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]