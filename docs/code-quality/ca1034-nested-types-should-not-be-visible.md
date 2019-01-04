---
title: CA1034. Вложенные типы не должны быть видимыми
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cce4f148311c301607c57a77aac46787e0578391
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890947"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034. Вложенные типы не должны быть видимыми

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Видимый извне тип содержит объявление видимый извне тип. Вложенных перечислений и защищенные типы будут исключены из этого правила.

## <a name="rule-description"></a>Описание правила
 Вложенный тип — это тип, объявленный внутри области другого типа. Вложенные типы полезны для инкапсуляции закрытых сведений о реализациях содержащего типа. В силу этого вложенные типы не должны быть видимыми для внешнего кода.

 Не используйте вложенные типы, видимые извне, для логической группировки или во избежание конфликтов имен. Вместо этого используйте пространства имен.

 Вложенные типы включают понятие доступности членов некоторые программисты не всегда очевидно.

 Защищенные типы могут использоваться в подклассы и вложенные типы в сценариях расширенной настройки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Если не предполагается вложенный тип, видимый извне, измените доступность типов. В противном случае удалите вложенного типа из его родительского элемента. Если вложение предназначена для категоризации вложенного типа, следует используйте пространство имен для создания иерархии.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило.

 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]