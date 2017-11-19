---
title: "CA2002: Не блокировать объекты со слабой идентификацией | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 54a7693f5e2921b7cab60278c870c456084c56f2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: не блокировать объекты со слабой идентификацией
|||  
|-|-|  
|TypeName|DoNotLockOnObjectsWithWeakIdentity|  
|CheckId|CA2002|  
|Категория|Microsoft.Reliability|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Поток пытается получить блокировку объекта со слабой идентификацией.  
  
## <a name="rule-description"></a>Описание правила  
 К объекту со слабой идентификацией может быть получен прямой доступ через границы домена приложения. Поток пытается получить блокировку объекта со слабой идентификацией, который может быть заблокирован вторым потоком в другом домене приложения, имеющим блокировку того же объекта. Следующие типы со слабой идентификацией и помечены правилом:  
  
-   <xref:System.MarshalByRefObject>  
  
-   <xref:System.ExecutionEngineException>  
  
-   <xref:System.OutOfMemoryException>  
  
-   <xref:System.StackOverflowException>  
  
-   <xref:System.String>  
  
-   <xref:System.Reflection.MemberInfo>  
  
-   <xref:System.Reflection.ParameterInfo>  
  
-   <xref:System.Threading.Thread>  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, используйте объект от типа, который не входит в список в разделе описания.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
## <a name="example"></a>Пример  
 В следующем примере показано несколько блокировок объекта, нарушающие правила.  
  
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Monitor>   
 <xref:System.AppDomain>   
 [Оператор lock](/dotnet/csharp/language-reference/keywords/lock-statement)   
 [Оператор SyncLock](/dotnet/visual-basic/language-reference/statements/synclock-statement)