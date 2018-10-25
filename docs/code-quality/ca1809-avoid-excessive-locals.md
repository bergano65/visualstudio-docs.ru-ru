---
title: 'CA1809: избегайте чрезмерного использования локальных переменных'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0135241e81fb020d5f5107bcb76e37bad16fb56d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828511"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: избегайте чрезмерного использования локальных переменных

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
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)