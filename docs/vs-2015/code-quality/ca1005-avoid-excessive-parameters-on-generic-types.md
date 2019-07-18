---
title: CA1005. Избегайте слишком много параметров в универсальных типах | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bc2986a81b0b21b2e2a4fd87b9c5a453e7d05c32
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704300"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005. Не используйте слишком много параметров в универсальных типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне универсальный тип имеет более двух параметров типа.

## <a name="rule-description"></a>Описание правила
 Чем больше параметров типов содержит универсальный тип, тем сложнее знать и запоминать, что представляет каждый параметр типа. Обычно ситуация очевидна при использовании одного параметра типа, как и в `List<T>`и в некоторых случаях с двумя параметрами типа, как и в `Dictionary<TKey, TValue>`. Если существует более двух параметров типа, сложность становится слишком большим для большинства пользователей (например, `TooManyTypeParameters<T, K, V>` в C# или `TooManyTypeParameters(Of T, K, V)` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените структуру использовать не более двух параметров типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если просто необходимо использовать более двух параметров типа. Использование универсальных типов в синтаксисе, который прост для понимания и использования сокращает время, необходимое для обучения и увеличивает скорость внедрения новых библиотек.

## <a name="related-rules"></a>Связанные правила
 [CA1010: Коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Не вкладывайте универсальные типы в сигнатурах членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Используйте универсальные типы в том случае, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
