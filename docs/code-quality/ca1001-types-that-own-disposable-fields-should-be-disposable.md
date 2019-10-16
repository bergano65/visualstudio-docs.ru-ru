---
title: 'CA1001: типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми'
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
ms.openlocfilehash: e8f2f313dad5f412a1a4d983d785caad5e6022a8
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349449"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое значение, если тип не виден за пределами сборки.<br /><br /> Критическое — если тип видим за пределами сборки.|

## <a name="cause"></a>Причина
Класс объявляет и реализует поле экземпляра, которое является типом <xref:System.IDisposable?displayProperty=fullName>, а класс не реализует <xref:System.IDisposable>.

## <a name="rule-description"></a>Описание правила
Класс реализует интерфейс <xref:System.IDisposable> для удаления неуправляемых ресурсов, которыми он владеет. Поле экземпляра, имеющее тип @no__t 0, указывает, что поле владеет неуправляемым ресурсом. Класс, объявляющий поле <xref:System.IDisposable>, косвенно владеет неуправляемым ресурсом и должен реализовать интерфейс <xref:System.IDisposable>. Если класс не владеет напрямую какими-либо неуправляемыми ресурсами, он не должен реализовывать метод завершения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, реализуйте <xref:System.IDisposable> и из метода <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызовите метод <xref:System.IDisposable.Dispose%2A> поля.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показан класс, нарушающий правило, и класс, который удовлетворяет правилу, путем реализации <xref:System.IDisposable>. Класс не реализует метод завершения, поскольку класс не владеет неуправляемыми ресурсами напрямую.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213.md)

[CA2216: высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216.md)

[CA2215: методы Dispose должны вызывать такие же методы базового класса](../code-quality/ca2215.md)

[CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)