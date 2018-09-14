---
title: CA1802. Используйте литералы там, где возможно
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 13cfc8b090d289173975b0ef2ee55562955de0c8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548755"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802. Используйте литералы там, где возможно

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Поле объявляется `static` и `readonly` (`Shared` и `ReadOnly` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) и инициализируется со значением, вычисляемым во время компиляции.

## <a name="rule-description"></a>Описание правила
 Значение `static``readonly` поля вычисляется во время выполнения, когда вызывается статический конструктор для объявляющего типа. Если `static``readonly` поле инициализируется, когда он объявляется и статический конструктор не был объявлен явно, компилятор выдает статический конструктор для инициализации поля.

 Значение `const` поля вычисляется во время компиляции и хранится в метаданных, что повышает производительность во время выполнения, сравнивая со `static``readonly` поля.

 Так как значение, присвоенное конечному полю, вычисляется во время компиляции, замените объявление на `const` таким образом, чтобы значение вычисляется во время компиляции, а не во время выполнения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, замените `static` и `readonly` модификаторы с `const` модификатор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, или отключите правило, в тех случаях, если производительность не имеет значения.

## <a name="example"></a>Пример
 В следующем примере показано типом, `UseReadOnly`, который нарушает правило и тип `UseConstant`, соответствующий этому правилу.

 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]