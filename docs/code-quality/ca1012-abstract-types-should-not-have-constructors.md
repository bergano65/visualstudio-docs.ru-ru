---
title: CA1012. Абстрактные типы не должны иметь конструкторы
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 182a0fc2b0d8947e6e77d557679d5ad92e5bb443
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929132"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012. Абстрактные типы не должны иметь конструкторы

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип является абстрактным и имеет открытый конструктор.

## <a name="rule-description"></a>Описание правила
 Конструкторы абстрактных типов могут быть вызваны только производными типами. Открытые конструкторы создают экземпляры типа. Невозможно создавать экземпляры абстрактного типа; абстрактный тип с открытым конструктором является недопустимым.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, защищать конструктор, или не объявите тип как абстрактный.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Абстрактный тип имеет открытый конструктор без параметров.

## <a name="example"></a>Пример
 Следующий пример содержит абстрактный тип, который нарушает это правило.

 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

## <a name="example"></a>Пример
 В следующем примере устраняется нарушение устраняется путем изменения специальных возможностей конструктора из `public` для `protected`.

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]