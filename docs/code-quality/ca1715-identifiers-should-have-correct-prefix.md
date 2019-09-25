---
title: CA1715. Идентификаторы должны иметь правильные префиксы
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7323fd044675eda2f528788ffc40943d071bf12b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234077"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715. Идентификаторы должны иметь правильные префиксы

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое — при срабатывании интерфейсов.<br /><br /> Не критическое — при возникновении параметров универсального типа.|

## <a name="cause"></a>Причина:

Имя интерфейса не начинается с прописной буквы I.

\- или -

Имя [параметра универсального типа](/dotnet/csharp/programming-guide/generics/generic-type-parameters) в типе или методе не начинается с прописной буквы 'T '.

По умолчанию это правило рассматривает только внешние видимые интерфейсы, типы и методы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

По соглашению имена некоторых программных элементов начинаются с определенного префикса.

Имена интерфейсов должны начинаться с прописной буквы "I", за которой следует другая прописная буква. Это правило сообщает о нарушениях имен интерфейсов, таких как "Минтерфаце" и "Исолатединтерфаце".

Имена параметров универсального типа должны начинаться с прописной буквы «'T», а при необходимости может следовать еще одна прописная буква. Это правило сообщает о нарушениях имен параметров универсального типа, таких как "V" и "Type".

Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, какие части кода будет анализировать это правило. Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Параметры типа с одним символом

Вы можете указать, следует ли исключать из этого правила параметры типа из одного символа. Например, чтобы указать, что это правило *не должно* анализировать параметры односимвольного типа, добавьте одну из следующих пар "ключ-значение" в editorconfig-файл в проекте:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Это правило никогда не срабатывает для параметра типа с `T`именем, `Collection<T>`например.

### <a name="api-surface"></a>Поверхность API

Вы можете настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca1715.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (именование).

## <a name="how-to-fix-violations"></a>Устранение нарушений

Переименуйте идентификатор таким образом, чтобы он был правильно исправлен.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

## <a name="interface-naming-example"></a>Пример именования интерфейса

В следующем фрагменте кода показан неверно именованный интерфейс:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

Следующий фрагмент кода устраняет предыдущее нарушение, добавляя к интерфейсу префикс "I":

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Пример именования параметра типа

В следующем фрагменте кода показан неправильно именованный параметр универсального типа:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

Следующий фрагмент кода устраняет предыдущее нарушение, представив префикс параметра универсального типа с помощью 'T ':

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Связанные правила

- [CA1722 Идентификаторы не должны иметь неверный префикс](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)