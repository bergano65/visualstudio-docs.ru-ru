---
title: CA1043. Используйте целый или строковый аргумент для индексаторов
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 298c92263903c3799f1e7e184a554f896366566c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235842"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043. Используйте целый или строковый аргумент для индексаторов

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Тип содержит индексатор, использующий <xref:System.Int32?displayProperty=fullName>тип индекса <xref:System.Object?displayProperty=fullName>, отличный от, <xref:System.Int64?displayProperty=fullName>, или <xref:System.String?displayProperty=fullName>.

По умолчанию это правило рассматривает только открытые и защищенные типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Индексаторы, то есть индексированные свойства, должны использовать целочисленный или строковый тип для индекса. Эти типы обычно используются для индексирования структур данных и повышения удобства использования библиотеки. <xref:System.Object> Использование типа должно быть ограничено теми случаями, когда конкретный целочисленный или строковый тип не может быть указан во время разработки. Если для создания индекса требуются другие типы, проверьте, представляет ли тип логическое хранилище данных. Если он не представляет логическое хранилище данных, используйте метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените индекс на целочисленный или строковый тип или используйте вместо индексатора метод.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Подавлять предупреждение из этого правила только после тщательного рассмотрения необходимости в нестандартном индексаторе.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1043.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (конструктор). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере показан индексатор, использующий <xref:System.Int32> индекс.

[!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
[!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
[!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA1023: Индексаторы не должны быть многомерными](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)
- [CA1024 Используйте свойства там, где это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)