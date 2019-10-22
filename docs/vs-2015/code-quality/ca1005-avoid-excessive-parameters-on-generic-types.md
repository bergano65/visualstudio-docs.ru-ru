---
title: 'CA1005: Избегайте чрезмерного числа параметров в универсальных типах | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7e75b2e295a561e026b437b3c62724536a3ac64e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671989"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: не используйте слишком много параметров в универсальных типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Внешний видимый универсальный тип имеет более двух параметров типа.

## <a name="rule-description"></a>Описание правила
 Чем больше параметров типов содержит универсальный тип, тем сложнее знать и запоминать, что представляет каждый параметр типа. Обычно очевидно с одним параметром типа, как в `List<T>`, и в некоторых случаях с двумя параметрами типа, как в `Dictionary<TKey, TValue>`. Если существует более двух параметров типа, сложность стала слишком отличной для большинства пользователей (например, `TooManyTypeParameters<T, K, V>` в C# или `TooManyTypeParameters(Of T, K, V)` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените структуру так, чтобы использовалось не более двух параметров типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если только проект не требует абсолютной необходимости более двух параметров типа. Предоставление универсальных шаблонов в синтаксисе, который легко понять и использовать, сокращает время, необходимое для изучения и увеличения скорости внедрения новых библиотек.

## <a name="related-rules"></a>Связанные правила
 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: используйте универсальные объекты, если это уместно](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>См. также раздел
 [Универсальные шаблоны](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
