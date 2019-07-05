---
title: CA2213. Следует высвобождать высвобождаемые поля | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cbb606729fe89eb5c2ebe3c814096ef39120836a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685253"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213. Следует высвобождать высвобождаемые поля
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName> объявляет поля, имеющие типы, которые также реализуют <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Не вызывается метод поля <xref:System.IDisposable.Dispose%2A> метод объявляющего типа.

## <a name="rule-description"></a>Описание правила
 Тип несет ответственность за освобождение все неуправляемые ресурсы; Это достигается путем реализации <xref:System.IDisposable>. Это правило проверяет, является ли уничтожаемого типа `T` объявляет поле `F` , являющийся экземпляром уничтожаемого типа `FT`. Для каждого поля `F`, правило пытается найти вызов `FT.Dispose`. Правило выполняет поиск методов, вызываемых `T.Dispose`и один уровень вниз (методы, вызываемые методы, вызываемые `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите <xref:System.IDisposable.Dispose%2A> для полей, типов, реализующих <xref:System.IDisposable> Если вы несете ответственность за выделение и освобождение неуправляемых ресурсов, содержащихся в полях.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если вы не несете ответственность за освобождение ресурсов, содержащихся в полях, или в том случае, если вызов <xref:System.IDisposable.Dispose%2A> происходит на более глубоком уровне вызывающего, чем правило проверки.

## <a name="example"></a>Пример
 В следующем примере показано типом `TypeA` , реализующий <xref:System.IDisposable> (`FT` в описании выше).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Пример
 В следующем примере показано типом `TypeB` , нарушает это правило, объявив поле `aFieldOfADisposableType` (`F` в описании выше) как уничтожаемого типа (`TypeA`) без вызова <xref:System.IDisposable.Dispose%2A> по полю. `TypeB` соответствует `T` в предыдущем описании.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.IDisposable?displayProperty=fullName> [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
