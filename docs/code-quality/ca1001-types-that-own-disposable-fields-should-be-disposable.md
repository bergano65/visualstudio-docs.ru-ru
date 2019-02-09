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
ms.openlocfilehash: 581bc75c22326275dcb3657910f60c2977094037
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907170"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001. Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Категория|Microsoft.Design|
|Критическое изменение|Non критическое, если тип не видимый за пределами сборки.<br /><br /> Критическое, если тип видим за пределами сборки.|

## <a name="cause"></a>Причина
 В классе объявляется и реализуется поле экземпляра, который является <xref:System.IDisposable?displayProperty=fullName> типа и класса не реализует <xref:System.IDisposable>.

## <a name="rule-description"></a>Описание правила
 Класс реализует <xref:System.IDisposable> интерфейс, чтобы освободить неуправляемые ресурсы, удерживаемые им. Поля экземпляра, <xref:System.IDisposable> тип указывает, что поле владеет неуправляемым ресурсом. Класс, который объявляет <xref:System.IDisposable> поле неявно владеет неуправляемым ресурсом и должен реализовывать <xref:System.IDisposable> интерфейс. Если класс не владеет непосредственно неуправляемые ресурсы, он не должен реализовывать метод завершения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте <xref:System.IDisposable> и из <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызов метода <xref:System.IDisposable.Dispose%2A> метод поля.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано, класс, который нарушает правило и класс, соответствующий этому правилу, реализовав <xref:System.IDisposable>. Класс не реализует метод завершения, так как этот класс не владеет неуправляемых ресурсов.

 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Методы Dispose должны вызывать метод dispose базового класса](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)