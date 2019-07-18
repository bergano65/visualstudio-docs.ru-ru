---
title: CA2213. Следует высвобождать высвобождаемые поля
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38157fcc23561b47a919151aa78a71f98b3909b
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805000"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213. Следует высвобождать высвобождаемые поля

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Тип, реализующий <xref:System.IDisposable?displayProperty=fullName> объявляет поля, имеющие типы, которые также реализуют <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Не вызывается метод поля <xref:System.IDisposable.Dispose%2A> метод объявляющего типа.

## <a name="rule-description"></a>Описание правила

Тип несет ответственность за освобождение все неуправляемые ресурсы. Правило проверяет CA2213 ли уничтожаемого типа (то есть, реализующий <xref:System.IDisposable>) `T` объявляет поле `F` , являющийся экземпляром уничтожаемого типа `FT`. Для каждого поля `F` , назначенный локально созданного объекта в методах или инициализаторы содержащего типа `T`, правило пытается найти вызов `FT.Dispose`. Правило выполняет поиск методов, вызываемых `T.Dispose` и один уровень ниже (то есть методы, вызываемые методы, вызываемые `T.Dispose`).

> [!NOTE]
> Отличное от [особые случаи](#special-cases), правило CA2213 активируется только для полей, которые назначаются локально созданный удаляемого объекта в инициализаторы и методы этого типа. Если объект создан или назначенные за пределами типа `T`, правило не срабатывает. Это снижает шум в случаях, где вмещающий тип не является владельцем ответственность за освобождение объекта.

### <a name="special-cases"></a>Особые случаи

CA2213 правило, также могут запускать для полей следующих типов, даже если локально не создается объект, который им были назначены:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Указывает, передаче объекта одного из этих типов в конструктор и назначив его к полю *dispose передачи права владения* для вновь сконструированного типа. То есть вновь сконструированный тип теперь несет ответственность за освобождение объекта. Если объект не удален, возникает нарушение CA2213.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите <xref:System.IDisposable.Dispose%2A> для полей, типов, реализующих <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Можно безопасно подавить предупреждение из этого правила, если:

- Помеченные тип не несет ответственности освобождения ресурса удерживаемые поле (то есть не имеет тип *dispose владения*)
- Вызов <xref:System.IDisposable.Dispose%2A> происходит на более глубоком уровне вызывающего, чем правило проверки

## <a name="example"></a>Пример

В следующем фрагменте показан тип `TypeA` , реализующий <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

В следующем фрагменте показан тип `TypeB` , нарушает правило CA2213, объявив поле `aFieldOfADisposableType` как уничтожаемого типа (`TypeA`) без вызова <xref:System.IDisposable.Dispose%2A> по полю.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>См. также

- <xref:System.IDisposable?displayProperty=fullName>
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)