---
title: 'CA1001: типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3def21cf32dd45c006045a5301293da2a5d0f70
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми
|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое — если тип не отображается за пределами сборки.<br /><br /> Критическое, если тип, видимый за пределами сборки.|

## <a name="cause"></a>Причина
 В классе объявляется и реализуется поле экземпляра, который является <xref:System.IDisposable?displayProperty=fullName> типа и класса не реализует <xref:System.IDisposable>.

## <a name="rule-description"></a>Описание правила
 Класс реализует <xref:System.IDisposable> интерфейс, чтобы освободить неуправляемые ресурсы, которыми владеет. Поле экземпляра, <xref:System.IDisposable> тип указывает, что поле владеет неуправляемым ресурсом. Класс, объявляющий <xref:System.IDisposable> поле неявно владеет неуправляемым ресурсом и должен реализовывать <xref:System.IDisposable> интерфейса. Если класс не владеет непосредственно все неуправляемые ресурсы, он не должен реализовывать метод завершения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, реализуйте <xref:System.IDisposable> и из <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызов метода <xref:System.IDisposable.Dispose%2A> метод поля.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В примере показан класс, который нарушает правило и класс, соответствующий этому правилу, реализовав <xref:System.IDisposable>. Класс не реализует метод завершения, так как класс не владеет непосредственно все неуправляемые ресурсы.

 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: методы Dispose должны вызывать такие же методы базового класса](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: типы, которым принадлежат собственные ресурсы, должны быть высвобождаемыми](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)