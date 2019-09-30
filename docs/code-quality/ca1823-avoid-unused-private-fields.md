---
title: CA1823. Избегайте неиспользуемых частных полей
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f0aa23ff93e193ee06509c1cb635404ec827793
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233363"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823. Избегайте неиспользуемых частных полей

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Это правило сообщается, когда закрытое поле в коде существует, но не используется ни одним из путей кода.

## <a name="rule-description"></a>Описание правила
Обнаружены закрытые поля, доступ к которым, судя по всему, не предоставляется в сборке.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, удалите поле или добавьте код, который его использует.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
В этом правиле можно отключить вывод предупреждений.

## <a name="related-rules"></a>Связанные правила
[CA1812 Избегайте использования внутренних классов без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Проверка неиспользуемых параметров](../code-quality/ca1801-review-unused-parameters.md)

[CA1804 Удалить неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)

[CA1811 Избегайте невызванного закрытого кода](../code-quality/ca1811-avoid-uncalled-private-code.md)