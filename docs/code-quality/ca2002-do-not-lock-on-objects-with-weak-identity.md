---
title: 'CA2002: Не блокировать объекты со слабой идентификацией | Документы Microsoft'
ms.custom: ''
ms.date: 01/31/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d509de487bd81b4401195a8e3564c165a2d50f0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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

К объекту со слабой идентификацией может быть получен прямой доступ через границы домена приложения. Поток пытается получить блокировку объекта со слабой идентификацией, который может быть заблокирован вторым потоком в другом домене приложения, имеющим блокировку того же объекта.

Следующие типы со слабой идентификацией и помечены правилом:

- <xref:System.String>

- Массивов типов значений, включая [целочисленные типы](/dotnet/csharp/language-reference/keywords/integral-types-table), [типов с плавающей запятой](/dotnet/csharp/language-reference/keywords/floating-point-types-table), и <xref:System.Boolean>.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

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
[lock-оператор (C#)](/dotnet/csharp/language-reference/keywords/lock-statement)  
[Оператор SyncLock (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)