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
ms.openlocfilehash: f4dbafb4c6f7ad590244842ac3def0e26f8a14fd
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57872970"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802. По возможности используйте литералы

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Поле объявляется `static` и `readonly` (`Shared` и `ReadOnly` в Visual Basic) и инициализируется со значением, вычисляемым во время компиляции.

По умолчанию это правило считывает только видимое извне поля, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Значение `static readonly` поля вычисляется во время выполнения, когда вызывается статический конструктор для объявляющего типа. Если `static readonly` поле инициализируется, когда он объявляется и статический конструктор не был объявлен явно, компилятор выдает статический конструктор для инициализации поля.

Значение `const` поля вычисляется во время компиляции и хранится в метаданных, что повышает производительность во время выполнения, сравнивая со `static readonly` поля.

Так как значение, присвоенное конечному полю, вычисляется во время компиляции, замените объявление на `const` таким образом, чтобы значение вычисляется во время компиляции, а не во время выполнения.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, замените `static` и `readonly` модификаторы с `const` модификатор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Это безопасно подавить предупреждение из этого правила, или отключите правило, в тех случаях, если производительность не имеет значения.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1802.api_surface = private, internal
```

В этой категории (производительность), можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показано типом, `UseReadOnly`, который нарушает правило и тип `UseConstant`, соответствующий этому правилу.

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]