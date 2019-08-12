---
title: CA1001. Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fae67f8c1ffa3b4e6d7cc2f0fbbaf670733f9ff4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923312"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001. Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое значение, если тип не виден за пределами сборки.<br /><br /> Критическое — если тип видим за пределами сборки.|

## <a name="cause"></a>Причина
Класс объявляет и реализует поле экземпляра, которое является <xref:System.IDisposable?displayProperty=fullName> типом, а класс не реализует. <xref:System.IDisposable>

## <a name="rule-description"></a>Описание правила
Класс реализует <xref:System.IDisposable> интерфейс для удаления неуправляемых ресурсов, которыми он владеет. Поле экземпляра, которое является <xref:System.IDisposable> типом, указывает, что поле владеет неуправляемым ресурсом. Класс, объявляющий <xref:System.IDisposable> поле, неявно владеет неуправляемым ресурсом и должен <xref:System.IDisposable> реализовывать интерфейс. Если класс не владеет напрямую какими-либо неуправляемыми ресурсами, он не должен реализовывать метод завершения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, реализуйте <xref:System.IDisposable> и <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> из метода вызовите <xref:System.IDisposable.Dispose%2A> метод поля.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показан класс, нарушающий правило, и класс, который удовлетворяет правилу путем реализации <xref:System.IDisposable>. Класс не реализует метод завершения, поскольку класс не владеет неуправляемыми ресурсами напрямую.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

[CA2216: Удаляемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA2215 Методы Dispose должны вызывать базовый класс Dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

[CA1049 Типы, владеющие собственными ресурсами, должны быть уничтожены](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)