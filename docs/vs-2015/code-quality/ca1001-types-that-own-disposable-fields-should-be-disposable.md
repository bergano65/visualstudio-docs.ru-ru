---
title: 'CA1001: типы, которым принадлежат освобождаемые поля, должны быть уничтожены | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dab4532f082bd81eaa7b812eb038c5957636d453
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548321"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001. Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое значение, если тип не виден за пределами сборки.<br /><br /> Критическое — если тип видим за пределами сборки.|

## <a name="cause"></a>Причина
 Класс объявляет и реализует поле экземпляра, которое является <xref:System.IDisposable?displayProperty=fullName> типом, а класс не реализует <xref:System.IDisposable> .

## <a name="rule-description"></a>Описание правила
 Класс реализует <xref:System.IDisposable> интерфейс для удаления неуправляемых ресурсов, которыми он владеет. Поле экземпляра, которое является <xref:System.IDisposable> типом, указывает, что поле владеет неуправляемым ресурсом. Класс, объявляющий поле, <xref:System.IDisposable> неявно владеет неуправляемым ресурсом и должен реализовывать <xref:System.IDisposable> интерфейс. Если класс не владеет напрямую какими-либо неуправляемыми ресурсами, он не должен реализовывать метод завершения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте <xref:System.IDisposable> и из <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> метода вызовите <xref:System.IDisposable.Dispose%2A> метод поля.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан класс, нарушающий правило, и класс, который удовлетворяет правилу путем реализации <xref:System.IDisposable> . Класс не реализует метод завершения, поскольку класс не владеет неуправляемыми ресурсами напрямую.

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2213. Следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216. Высвобождаемые типы должны объявлять методы завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215. Метод Dispose должен вызывать базовый класс Dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049. Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
