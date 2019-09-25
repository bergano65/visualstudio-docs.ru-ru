---
title: CA1034. Вложенные типы не должны быть видимыми
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ead932af202bd1a44464025a1b09baa698acb7b1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236032"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034. Вложенные типы не должны быть видимыми

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Видимый извне тип содержит объявление видимого извне типа. Из этого правила исключены вложенные перечисления и защищенные типы.

## <a name="rule-description"></a>Описание правила
Вложенный тип — это тип, объявленный в области другого типа. Вложенные типы полезны для инкапсуляции закрытых сведений о реализации содержащего типа. В силу этого вложенные типы не должны быть видимыми для внешнего кода.

Не используйте внешние видимые вложенные типы для логической группировки или избежание конфликтов имен. Вместо этого используйте пространства имен.

Вложенные типы включают понятие доступности членов, которые некоторые программисты не понимают четко.

Защищенные типы можно использовать в подклассах и вложенных типах в сценариях предварительной настройки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Если вложенный тип не должен быть видимым извне, измените доступность типа. В противном случае удалите вложенный тип из его родителя. Если целью вложенности является категоризация вложенного типа, используйте пространство имен для создания иерархии.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий правило.

[!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
[!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]