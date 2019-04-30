---
title: CA2213. Следует высвобождать высвобождаемые поля
ms.date: 11/05/2018
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
ms.openlocfilehash: 1fff209c9a432b78ce27e9c344c1afd29e93d57f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806684"
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

Тип несет ответственность за освобождение все неуправляемые ресурсы. Правило проверяет CA2213 ли уничтожаемого типа (то есть, реализующий <xref:System.IDisposable>) `T` объявляет поле `F` , являющийся экземпляром уничтожаемого типа `FT`. Для каждого поля `F` , назначенный локально созданного объекта в методах или инициализаторы содержащего типа `T`, правило пытается найти вызов `FT.Dispose`. Правило выполняет поиск методов, вызываемых `T.Dispose` и один уровень ниже (то есть методы, вызываемые методы, вызываемые `FT.Dispose`).

> [!NOTE]
> CA2213 правило срабатывает, только для полей, которые назначаются локально созданный удаляемого объекта в инициализаторы и методы этого типа. Если объект создан или назначенные за пределами типа `T`, правило не срабатывает. Это снижает шум в случаях, где вмещающий тип не является владельцем ответственность за освобождение объекта.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите <xref:System.IDisposable.Dispose%2A> для полей, типов, реализующих <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Это безопасно подавить предупреждение из этого правила, если вы не несете ответственность, для освобождения ресурсов, содержащихся в полях, или если вызов <xref:System.IDisposable.Dispose%2A> происходит на более глубоком уровне вызывающего, чем правило проверки.

## <a name="example"></a>Пример

В следующем фрагменте показан тип `TypeA` , реализующий <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

В следующем фрагменте показан тип `TypeB` , нарушает правило CA2213, объявив поле `aFieldOfADisposableType` как уничтожаемого типа (`TypeA`) без вызова <xref:System.IDisposable.Dispose%2A> по полю.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>См. также

- <xref:System.IDisposable?displayProperty=fullName>
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)