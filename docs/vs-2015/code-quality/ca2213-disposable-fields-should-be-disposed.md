---
title: 'CA2213: освобождаются поля, которые должны быть удалены | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662898"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: следует высвобождать высвобождаемые поля
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName>, объявляет поля, которые относятся к типам, которые также реализуют <xref:System.IDisposable>. Метод <xref:System.IDisposable.Dispose%2A> поля не вызывается методом <xref:System.IDisposable.Dispose%2A> объявляющего типа.

## <a name="rule-description"></a>Описание правила
 Тип отвечает за удаление всех неуправляемых ресурсов; Это достигается путем реализации <xref:System.IDisposable>. Это правило проверяет, `T` ли удаляемый тип объявляет поле `F`, которое является экземпляром удаляемого типа `FT`. Для каждого поля `F` правило пытается нахождение вызова `FT.Dispose`. Правило ищет методы, вызываемые `T.Dispose`, и один уровень ниже (методы, вызываемые методами, вызываемыми `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите <xref:System.IDisposable.Dispose%2A> для полей типов, реализующих <xref:System.IDisposable> если вы отвечаете за выделение и освобождение неуправляемых ресурсов, удерживаемых полем.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если вы не несете ответственность за освобождение ресурса, удерживаемого полем, или если вызов <xref:System.IDisposable.Dispose%2A> происходит на более уровне более глубокого вызова, чем проверка правила.

## <a name="example"></a>Пример
 В следующем примере показан тип `TypeA`, который реализует <xref:System.IDisposable> (`FT` в предыдущем обсуждении).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Пример
 В следующем примере показан тип `TypeB`, нарушающий это правило, объявляя поле `aFieldOfADisposableType` (`F` в предыдущем обсуждении) в качестве высвобождаемого типа (`TypeA`) и не вызывает <xref:System.IDisposable.Dispose%2A> в поле. `TypeB` соответствует `T` в предыдущем обсуждении.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>См. также раздел
 [шаблон удаления](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) <xref:System.IDisposable?displayProperty=fullName>
