---
title: "CA1001: Типы, которым принадлежат освобождаемые поля, должны быть высвобождаемыми | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 30609be8b70f65cb48478c6d6d2c0f3b6d89a029
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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