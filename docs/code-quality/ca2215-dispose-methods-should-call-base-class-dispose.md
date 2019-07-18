---
title: CA2215. Метод Dispose должен вызывать базовый класс Dispose
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 203fc14097e0c6d2fbdaee1689deffdfe814eb63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541901"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215. Метод Dispose должен вызывать базовый класс Dispose

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName> наследует от типа, который также реализует <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Не вызывает метод наследующий тип <xref:System.IDisposable.Dispose%2A> метод родительского типа.

## <a name="rule-description"></a>Описание правила
 Если тип наследуется от уничтожаемого типа, он должен вызвать <xref:System.IDisposable.Dispose%2A> метод из базового типа в собственный <xref:System.IDisposable.Dispose%2A> метод. Вызов метода базового типа Dispose гарантирует, что освобождаются все ресурсы, созданные с базовым типом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите `base`.<xref:System.IDisposable.Dispose%2A> в вашей <xref:System.IDisposable.Dispose%2A> метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если вызов `base`.<xref:System.IDisposable.Dispose%2A> происходит на более глубоком уровне вызывающего, чем правило проверки.

## <a name="example"></a>Пример
 В следующем примере показано типом `TypeA` , реализующий <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Пример
 В следующем примере показано типом `TypeB` , производный от типа `TypeA` и правильно вызывает его <xref:System.IDisposable.Dispose%2A> метод.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>См. также

- <xref:System.IDisposable?displayProperty=fullName>
- [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)