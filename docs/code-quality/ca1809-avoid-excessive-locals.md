---
title: CA1809. Избегайте лишних локальных переменных
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4ac6947f8424c3b9aa7429ee378b4bb89be73ca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545245"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809. Избегайте лишних локальных переменных

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член содержит более 64 локальных переменных, некоторые из которых может быть созданный компилятором.

## <a name="rule-description"></a>Описание правила
 Обычно для оптимизации производительности рекомендуется хранить значение в регистр процессора, а не в памяти, что называется *регистре* значение. Среда CLR рассматривает до 64 локальных переменных в среде. Переменные, незарегистрированные помещаются в стек и должны быть перемещены Зарегистрируйтесь до манипуляции. Чтобы разрешить вероятность того, все локальные переменные регистрации, ограничить количество локальных переменных до 64.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, выполнить рефакторинг реализация, которую нужно использовать не более 64 локальных переменных.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, или отключить правило, если производительность не является проблемой.

## <a name="related-rules"></a>Связанные правила
 [CA1804: Удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)