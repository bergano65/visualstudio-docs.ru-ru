---
title: CA1505. Избегайте кода, неудобного для поддержки
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 017d7ec1b28c1a76b7a837a38f5089c95724fe97
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930718"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505. Избегайте кода, неудобного для поддержки

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Категория|Microsoft.Maintainability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип или метод имеет низкий индекс обслуживаемости.

## <a name="rule-description"></a>Описание правила
 Индекс удобства поддержки вычисляется с помощью следующих метрик: строки кода, объем программы и сложность организации циклов. Программа тома — это мера трудности понимания типа или метода, основанный на количестве операторов и операндов в коде. Сложность организации циклов — это мера сложности структурного типа или метода. Дополнительные сведения о метриках кода в [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/code-metrics-values.md).

 Низкий индекс обслуживаемости указывает, что тип или метод, вероятно, трудно поддерживать и будет хорошим кандидатом для переработки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, измените тип или метод и попробуйте разделить ее на сокращенный и более точный типы или методы.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Исключите это предупреждение, когда тип или метод по-прежнему считается простым в обслуживании, несмотря на своего большого размера или типа или метода нельзя разделить.

## <a name="see-also"></a>См. также

- [Предупреждения удобства обслуживания](../code-quality/maintainability-warnings.md)
- [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/code-metrics-values.md)