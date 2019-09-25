---
title: CA1506. Избегайте чрезмерной взаимозависимости классов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1721fd52c00c5b312c88f19d48b668b12d28f050
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234497"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506. Избегайте чрезмерной взаимозависимости классов

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Категория|Поддержка Microsoft.|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Тип или метод связан с множеством других типов.

## <a name="rule-description"></a>Описание правила

Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе.

Типы и методы, имеющие высокую степень взаимосвязей классов, могут быть трудно поддерживать. Рекомендуется использовать типы и методы, которые демонстрируют низкую связь и высокую степень связности.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить это нарушение, попытайтесь изменить тип или метод, чтобы уменьшить число типов, к которым он привязан.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Исключите это предупреждение, если тип или метод считается обслуживаемым, несмотря на большое количество зависимостей от других типов.

## <a name="see-also"></a>См. также

- [Предупреждения удобства обслуживания](../code-quality/maintainability-warnings.md)
- [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/code-metrics-values.md)