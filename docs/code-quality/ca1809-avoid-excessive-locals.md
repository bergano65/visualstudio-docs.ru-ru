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
ms.openlocfilehash: 8d1c2f76258be3b0be6409bffd002fd916883ab2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921540"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809. Избегайте лишних локальных переменных

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Элемент содержит более 64 локальных переменных, некоторые из которых могут создаваться компилятором.

## <a name="rule-description"></a>Описание правила
Распространенная оптимизация производительности заключается в хранении значения в регистре процессора, а не в памяти, которое называется *регистрирует* значением. Среда CLR считает до 64 локальных переменных для енрегистратион. Переменные, которые не енрегистеред, помещаются в стек и должны быть перемещены в регистр перед манипуляцией. Чтобы обеспечить возможность получения енрегистеред всеми локальными переменными, ограничьте число локальных переменных до 64.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, выполните рефакторинг реализации, чтобы использовать не более 64 локальных переменных.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила или отключать правило, если производительность не является проблемой.

## <a name="related-rules"></a>Связанные правила
[CA1804 Удалить неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)