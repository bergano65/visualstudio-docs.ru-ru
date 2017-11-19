---
title: "CA2215: Методы Dispose должны вызывать метод dispose базового класса | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0659b9ec82353e3c658f1ba89f07fad197dd8670
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: методы Dispose должны вызывать такие же методы базового класса
|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип, реализующий <xref:System.IDisposable?displayProperty=fullName> наследует от типа, который также реализует <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Не вызывает метод наследующий тип <xref:System.IDisposable.Dispose%2A> метод родительского типа.  
  
## <a name="rule-description"></a>Описание правила  
 Если тип наследуется от удаляемого типа, он должен вызвать <xref:System.IDisposable.Dispose%2A> метод базового типа из собственного <xref:System.IDisposable.Dispose%2A> метод. Вызов метода базового типа Dispose гарантирует, что освобождаются все ресурсы, созданные базовым типом.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, вызовите `base`.<xref:System.IDisposable.Dispose%2A> в ваш <xref:System.IDisposable.Dispose%2A> метод.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если вызов `base`.<xref:System.IDisposable.Dispose%2A> происходит на более глубоком уровне вызывающего, чем правила проверки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `TypeA` , реализующий <xref:System.IDisposable>.  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип `TypeB` , наследуемый от типа `TypeA` и правильно вызывает его <xref:System.IDisposable.Dispose%2A> метод.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Шаблон удаления](/dotnet/standard/design-guidelines/dispose-pattern)