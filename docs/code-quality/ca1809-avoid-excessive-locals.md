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
ms.openlocfilehash: ea0d1d27f583e86a62e9c0ff524d9d623253d007
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917344"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: избегайте чрезмерного использования локальных переменных
|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член содержит более 64 локальных переменных, некоторые из которых могут быть компилятором.

## <a name="rule-description"></a>Описание правила
 Обычно для оптимизации производительности — хранить значение в регистре процессора, а не в памяти, который называется *регистре* значение. Общеязыковая среда выполнения считает, что до 64 локальных переменных в среде. Незарегистрированные переменные помещаются в стек и должны быть перемещены Зарегистрируйтесь до обработки. Чтобы разрешить вероятность того, все локальные переменные регистрации, ограничить количество локальных переменных в 64.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, выполните рефакторинг реализация, которую нужно использовать не более 64 локальных переменных.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, или отключить правило, если производительность не является проблемой.

## <a name="related-rules"></a>Связанные правила
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)