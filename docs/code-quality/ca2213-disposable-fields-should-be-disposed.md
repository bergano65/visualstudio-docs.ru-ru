---
title: "CA2213: Следует высвобождать высвобождаемые поля | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4da3299e839be08a5ff11792aa2c80a364349b18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
 В следующем примере показано тип `TypeB` , нарушающий это правило, объявив поле `aFieldOfADisposableType` (`F` в описании выше) как удаляемого типа (`TypeA`) и не вызывает метод <xref:System.IDisposable.Dispose%2A> по полю. `TypeB`соответствует `T` в описании выше.  
  
 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)