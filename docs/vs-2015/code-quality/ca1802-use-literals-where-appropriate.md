---
title: CA1802. При необходимости использовать литералы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5990d8ea3720098651d3ed696f6ee5ff907b82f3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979168"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802. По возможности используйте литералы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Поле объявляется `static` и `readonly` (`Shared` и `ReadOnly` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) и инициализируется со значением, вычисляемым во время компиляции.

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

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
