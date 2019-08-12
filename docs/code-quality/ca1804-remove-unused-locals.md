---
title: CA1804. Удалите неиспользуемые локальные переменные
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bd3e9c56bb02995d9b99b57bb2799ab69b51a42d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921569"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804. Удалите неиспользуемые локальные переменные

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Метод объявляет локальную переменную, но не использует переменную, кроме случая, когда получатель оператора присваивания. Для анализа по этому правилу тестируемая сборка должна быть построена с отладочной информацией, а соответствующий файл базы данных программы (PDB) должен быть доступен.

## <a name="rule-description"></a>Описание правила
Неиспользуемые локальные переменные и ненужные присвоения увеличивают размер сборки и снижают производительность.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите или используйте локальную переменную.

> [!NOTE]
> C# Компилятор удаляет неиспользуемые локальные переменные, `optimize` если включен параметр.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Подавлять предупреждение из этого правила, если переменная была вызвана компилятором. Также можно отключить вывод предупреждений из этого правила или отключать правило, если производительность и обслуживание кода не являются основными проблемами.

## <a name="example"></a>Пример
В следующем примере показано несколько неиспользуемых локальных переменных.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA1809 Избегайте чрезмерного использования локальных переменных](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811 Избегайте невызванного закрытого кода](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812 Избегайте использования внутренних классов без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Проверка неиспользуемых параметров](../code-quality/ca1801-review-unused-parameters.md)