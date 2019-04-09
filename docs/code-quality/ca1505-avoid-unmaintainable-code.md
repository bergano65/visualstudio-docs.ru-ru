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
ms.openlocfilehash: 740ef26af6f1f84d23ef27de5176df1b3de98b34
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232500"
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

Индекс удобства поддержки вычисляется с помощью следующих метрик: строки кода, объем программы и сложность организации циклов. Программа тома — это мера трудности понимания типа или метода, основанный на количестве операторов и операндов в коде. Сложность организации циклов — это мера сложности структурного типа или метода. Дополнительные сведения о метриках кода в [меру сложности и удобства сопровождения управляемого кода](../code-quality/code-metrics-values.md).

Низкий индекс обслуживаемости указывает, что тип или метод, вероятно, трудно поддерживать и будет хорошим кандидатом для переработки.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить это нарушение, измените тип или метод и попробуйте разделить ее на сокращенный и более точный типы или методы.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Можно отключить это предупреждение, когда типа или метода нельзя разделить или является поддерживаемым несмотря на своего большого размера.

## <a name="see-also"></a>См. также

- [Предупреждения, связанные с удобством обслуживания](../code-quality/maintainability-warnings.md)
- [Меру сложности и удобства сопровождения управляемого кода](../code-quality/code-metrics-values.md)