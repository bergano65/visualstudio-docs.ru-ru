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
ms.openlocfilehash: b655609548d3de293abe2adc0ec3fb5c6fcf297b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59232487"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506. Избегайте чрезмерной взаимозависимости классов

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Категория|Microsoft.Maintainability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Тип или метод связана с другими типами.

## <a name="rule-description"></a>Описание правила

Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе.

Типы и методы, которые с высокой степенью взаимозависимости классов может быть трудно поддерживать. Рекомендуется использовать типы и методы, которые характерны для нижнее связи и высокой связности.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить это нарушение, попробуйте изменить тип или метод, чтобы уменьшить количество типов, к которым она связана.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Исключите это предупреждение, когда тип или метод является поддерживаемым несмотря на большое количество зависимостей от других типов.

## <a name="see-also"></a>См. также

- [Предупреждения удобства обслуживания](../code-quality/maintainability-warnings.md)
- [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/code-metrics-values.md)