---
title: CA1802. По возможности используйте литералы
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c6512f02d13c2eeb441f5b374c4785deffe22a22
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547064"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802. По возможности используйте литералы

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Поле объявляется `static` и `readonly` (`Shared` и `ReadOnly` в Visual Basic) и инициализируется со значением, вычисляемым во время компиляции.

По умолчанию это правило рассматривает только видимые извне поля, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Значение `static readonly` поля вычисляются во время выполнения, когда вызывается статический конструктор для объявляющего типа. `static readonly` Если поле инициализируется при объявлении и статический конструктор не объявлен явным образом, компилятор создает статический конструктор для инициализации поля.

Значение `const` поля вычисляются во время компиляции и сохраняется в метаданных, что повышает производительность среды выполнения при сравнении `static readonly` с полем.

Так как значение, назначенное целевому полю, вычисляемым во время компиляции, измените объявление на `const` поле, чтобы значение было вычислено во время компиляции, а не в среде выполнения.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, замените `static` модификаторы `const` и `readonly` модификатором.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно отключить вывод предупреждения из этого правила или отключать правило, если производительность не важна.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1802.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (производительность). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показан тип, `UseReadOnly`, который нарушает правило и `UseConstant`тип, который удовлетворяет правилу.

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]