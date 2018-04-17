---
title: 'CA2213: Следует высвобождать высвобождаемые поля | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 89f861db9c6e22492a8720a5890020cce26a4f43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: следует высвобождать высвобождаемые поля
|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName> , объявляет поля, которые относятся к типам, которые также реализуют <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Метод поля не вызывается <xref:System.IDisposable.Dispose%2A> метод объявляющего типа.  
  
## <a name="rule-description"></a>Описание правила  
 Тип отвечает за освобождение все неуправляемые ресурсы; Это достигается путем реализации <xref:System.IDisposable>. Это правило проверяет, является ли удаляемого типа `T` объявляет поле `F` который является экземпляром освобождаемого типа `FT`. Для каждого поля `F`, правило пытается найти вызов `FT.Dispose`. Правило выполняет поиск методов, вызываемых `T.Dispose`и один уровень вниз (методы, вызываемые методы, вызываемые `FT.Dispose`).  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, вызовите <xref:System.IDisposable.Dispose%2A> на поля, имеющие типы, реализующие <xref:System.IDisposable> Если вы несете ответственность за выделение и освобождение неуправляемых ресурсов, содержащихся в полях.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если вы не отвечает для освобождения ресурсов, содержащихся в полях, или вызов <xref:System.IDisposable.Dispose%2A> происходит на более глубоком уровне вызывающего, чем правила проверки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `TypeA` , реализующий <xref:System.IDisposable> (`FT` в описании previosu).  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `TypeB` , нарушающий это правило, объявив поле `aFieldOfADisposableType` (`F` в описании выше) как удаляемого типа (`TypeA`) и не вызывает метод <xref:System.IDisposable.Dispose%2A> по полю. `TypeB` соответствует `T` в описании выше.  
  
 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)